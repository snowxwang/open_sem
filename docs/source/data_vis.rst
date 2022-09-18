Data Visualization
==================

.. autosummary::
   :toctree: generated

Using Neuroglancer (ng)
-----------------------

Neuroglancer is a data visualization developed by Google. To set up Neuroglancer locally on your PC, please check out the tutorial here:

:doc:`/data_vis/ng_setup` section for setting up Neuroglancer on a Windows Machine

.. code-block:: console

   (.venv) $ pip install lumache
   

Using 3ds Max
-------------

To retrieve a list of random ingredients,
you can use the ``lumache.get_random_ingredients()`` function:

.. autofunction:: lumache.get_random_ingredients

The ``kind`` parameter should be either ``"meat"``, ``"fish"``,
or ``"veggies"``. Otherwise, :py:func:`lumache.get_random_ingredients`
will raise an exception.

.. autoexception:: lumache.InvalidKindError

For example:

>>> import lumache
>>> lumache.get_random_ingredients()
['shells', 'gorgonzola', 'parsley']
