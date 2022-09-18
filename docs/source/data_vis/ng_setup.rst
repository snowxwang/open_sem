Neuroglancer Setup on Windows Machines
======================================

Contributors: `Kelly Yin <https://github.com/Kelly-Yin>`_ and `Snow Wang <https://github.com/snowxwang>`_

.. autosummary::
   :toctree: generated


Prepare for ng installation
---------------------------

To prepare your Windows computer for ng installation, first install these applications:

- Install `Visual Studio <https://visualstudio.microsoft.com/downloads/>`_ - (download the free community version)
- Install `Anaconda <https://www.anaconda.com/products/individual>`_
- Install `Git <https://git-scm.com/download/win>`_ (call `Anaconda Prompt <https://docs.anaconda.com/anaconda/install/verify-install/>`_ or `Command Prompt <https://www.dell.com/support/kbdoc/en-in/000130703/the-command-prompt-what-it-is-and-how-to-use-it-on-a-dell-system>`_ in your window search option)

>>> conda install -c anaconda git


- Install `chocolatey <https://chocolatey.org/install>`_ 
    - `Open Windows PowerShell and run as Administrator <https://www.javatpoint.com/powershell-run-as-administrator>`_
    - In **PowerShell**, run:
    
    >>> Get-ExecutionPolicy
    
    - If it returns ``Restricted``, then run ``Set-ExecutionPolicy AllSigned`` or ``Set-ExecutionPolicy Bypass -Scope Process``.
    - In **PowerShell**, run:
    
    >>> Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
    
    - Now check if choco is installed. In **PowerShell**, type:
    
    >>> choco
    
    - If it returns the message below, you are ready to go.

- Install `nodejs <https://nodejs.org/en/download/>`_
    - In **PowerShell**, run:
    
    >>> choco install -y --force nodejs
    
    - If returns the message below, you are good to move on.
    - Test nodejs. In Command Prompt, run:
    
    >>> node -v
    
    - If it returns the message below, you are good to proceed.


Install Neuroglancer
--------------------

To install neuroglancer and the related components, we want to first create a new enviroment (let's call it ``ng_torch``) and install `PyTorch <https://pytorch.org/>`_ for it:


- Open **Anaconda Prompt** or **Command Prompt**, run:

>>> conda create -n ng_torch python=3.8
>>> activate ng_torch
>>> conda install pytorch torchvision cudatoolkit=11.0 -c pytorch

- Now check your PyTorch version (we need the version to be >1.80):

>>> pip3 show torch


- If you need to update ``pip`` in the virtual enviroment, run

>>> python -m pip install --user --upgrade pip


- Now use ``pip`` to install ng and other packages you need:

>>> pip install neuroglancer
>>> pip install jupyter  # (optional) jupyter/ipykernel installation
>>> pip install numpy Pillow requests tornado sockjs-tornado six google-apitools selenium imageio h5py cloud-volume
>>> python -m pip install -U scikit-image


- Make a folder for ng:

>>> mkdir project
>>> cd project
>>> git clone https://github.com/google/neuroglancer.git
>>> cd neuroglancer
>>> curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")" \
    [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"    # This loads nvm


- Install `npm <https://docs.npmjs.com/downloading-and-installing-node-js-and-npm>`_. In **Anaconda Prompt**, run:

>>> pip install npm

- After installation, run:

>>> npm i


- Finally, in **Anaconda Prompt**, run:

>>> python setup.py install

- If you encounter error messages in the last step, run this code before re-run the last line:

>>> npm run build-python-min


Use Jupyter Notebook to set up your ng viewer
---------------------------------------------

Open **Anaconda**, locate your ng enviroment and start a ``Jupyter Notebook``:


- In the notebook, run the code blocks in sequence:

.. code-block:: console
   
   import neuroglancer
   import numpy as np
   from skimage.io import imread
   import h5py
   import os


- Set up the local server:

.. code-block:: console

   ip = 'localhost'  # or public IP of the machine for sharable display
   port = 9999       # change to an unused port number
   neuroglancer.set_server_bind_address(bind_address=ip, bind_port=port)
   viewer=neuroglancer.Viewer()


- If your reconstruction has been exported as an image stack, this code loads your entire image folder. In this case, we are loading a folder named `jwr_pyr87` containing 773 image sections:

.. code-block:: console

   script_dir = os.path.abspath('') # locate the folder where the current script is being run
   sample_name = 'jwr_pyr87' # put your image folder in the script path and specify the name of the folder
   img_dir = os.path.join(script_dir, sample_name)
   img_idx = sorted(next(os.walk(img_dir))[2])
   num_of_img = len(img_idx)
   sample_height = 832 # specify the exported image size in x
   sample_length = 832 # specify the exported image size in y
   img_shape = (sample_height, sample_length)
   img_stack = np.zeros((len(img_idx),) + img_shape, dtype=np.int64) # allocate memory
   print(img_stack.shape)

   i = 0
   for i in range(num_of_img):
       
       img_stack[i] = imread(img_dir + "/" + img_idx[i])
       i += 1
   
   print(img_stack.shape) # read all the images exported from VAST into a single image stack


- If your reconstruction file is in .h5 format, use the code below to load your image stack:

.. code-block:: console

   with h5py.File('C:/Users/Lichtman Lab/Desktop/h5_data/jwr_pyr87.h5', 'r') as fl:
       
       img_stack = np.array(fl['images'])


- Set the x,y,z resolutions for the ng viewer:

.. code-block:: console

   res = neuroglancer.CoordinateSpace(
       names=['z', 'y', 'x'],
       units=['nm', 'nm', 'nm'],
       scales=[120, 256, 128]) # set the x,y,z resolutions for neuroglacer 


- Add a layer in ng viewer to show the segmentation/reconstruction:

.. code-block:: console

   def ngLayer(data, res, oo=[0,0,0], tt='segmentation'):
       
       return neuroglancer.LocalVolume(data, dimensions=res, volume_type=tt, voxel_offset=oo)


- Configure the ng layers: (in this case, we are loading a precomputed EM volume)

.. code-block:: console

   with viewer.txn() as s:
       s.layers['em'] = neuroglancer.ImageLayer(source='precomputed://https://rhoana.rc.fas.harvard.edu/ng/jwr15-120_im')
       s.layers.append(name='seg', layer=ngLayer(img_stack.astype(np.uint8), res, tt='segmentation'))


- Generate a link for your ng viewer:

.. code-block:: console

   print(viewer)


- Obtain the complete segment list for the segmentation layer:

.. code-block:: console

   np.unique(img_stack)


- Please feel free to download the sample Jupyter [notebook] or `Colab notebook <https://colab.research.google.com/drive/1OP3VSKOao0Wa6Z4RPGc2r38PM0oemzgt?usp=sharing>`_ whichever is convenient for you.