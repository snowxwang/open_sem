Tutorials for Serial Electron Microscopy (SEM)
===================================================

**Open SEM** is a site providing free tutorials for serial electron microscopy (SEM), EM datasets, and open code for image processing and data analysis.

This repository provides computational tools for practicing biologists to analyze volumetric image data at large-scale. These tools focus on in-depth analyses *after* automatic/semi-automatic segmentation. We use examples of 3D data acquired from serial electron microscopy for demonstrations, but all the codes and scripts should be able to deal with other types of 3D images such as fluorescence microscopy image stacks.

The intended audience is the *practicing biologists/neuroscientists* - e.g., the students, researchers, and clinicians collecting volumeric image data in the hospital or laboratory. Some sections of this material can get pretty math-heavy, but we have tried to outline the main concepts as directly as possible, with hands-on implementations of all concepts.


.. note::

   This project is under active development.


Contents
--------

This site provides information and resources for dealing with images acquired using Serial Electron Microscopy. We are presnting the entire computational pipeline here. 


Contributors
------------

This repository is created by `Snow Wang <https://www.snowxwang.com>`_. Core developers and their contributions are listed below:


- Website Building & Contents Creation: Snow, `Zhirui (Ray) Shen <https://github.com/rayer0>`_
- Microscopy Tutorials: Snow, `Yulan (Mumu) Fang <https://github.com/MumuFang>`_
- EM Tutorials: Snow
- Image Processing Tutorials: Snow
- Data Analysis: Snow, `Yutian (Tim) Fan <https://github.com/Anominious>`_, `Wenjie (Kelly) Yin <https://github.com/Kelly-Yin>`_
- Data Visualization: `Bowen Gong <https://github.com/BowenGong2000>`_, Kelly, Snow

Former Contributors: `Bowen (Nola) Zheng <https://github.com/zheng545>`_, `Ruilin Cai <https://github.com/RuilinC>`_


Supported Image Data
--------------------

All the tools presented in this repository are designed to process or visualize annotated 3D datasets exhibiting the following features:

- labeled/segmented serial cross-sectional images
- segmentation files are sequence of 8-bit, 16-bit, or 24-bit grayscale images
- .PNG files are preferred


Supported Languages & Software
------------------------------

- Python
- MATLAB
- VAST
- 3ds Max


Related Projects
----------------

- `3D reconstruction of mitochondria <https://snowxwang.github.io/mito/>`_
- JWR15 Project



   
.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Microscopy

   /microscopy/digital_image
   /microscopy/electron_microscopy
   /microscopy/serial_em


.. toctree::
   :maxdepth: 3
   :hidden:
   :caption: Ultrastructure of the Cell

   /cell/cell_in_em
   /cell/cell_organelles
   /cell/neurons_in_em


.. toctree::
   :maxdepth: 3
   :hidden:
   :caption: Image Processing

   /image_processing/alignment
   /image_processing/segmentation
   /image_processing/feature_detection


.. toctree::
   :maxdepth: 3
   :hidden:
   :caption: Data Analysis

   /data_analysis/annotation
   /data_analysis/proofreading
   /data_analysis/vast_export


.. toctree::
   :maxdepth: 3
   :hidden:
   :caption: Data Visualization

   /data_vis/ng_setup
   /data_vis/3dmax

