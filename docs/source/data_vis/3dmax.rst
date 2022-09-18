3D Rendering Using 3ds Max 
==========================

Contributors: `Bowen Gong <https://github.com/BowenGong2000>`_ and `Kelly Yin <https://github.com/Kelly-Yin>`_

.. autosummary::
   :toctree: generated

Animation
---------

In this section, we are going to create a rotation animation using the software 3ds Max. When complete, this animation will allow you to demonstrate your object in 360 degrees with controllable speed, framerate, and resolution. For instance, the short gif below demonstrates 4 parts of a block of brain cells of rat, each rotates 360 degrees and lasts for 10 seconds. 


.. figure:: /_static/images/3dmax_mito.gif
   :width: 60%
   :align: center
   :alt: reconstructed mitochondria from a SEM volume


Nonetheless, this tutorial will allow you to create a similar animation above, demonstrating anything you want, and you can expect a higher resolution and frame rate for your work since this file is compressed for convenience. 


Overview & Introduction
-----------------------

There is something important we need to mention before we start the actual procedure. 


+ The software, 3ds Max is a **Windows-only** software, so please get a pc. More importantly, we do recommend that you use a computer with a discrete graphics card and better have **RAM larger or equal to 16G**. 
+ You don’t need any background knowledge to fluently complete this section.
+ You can get a **free license** of the software if you work for an academic institute or are a student, you can get the free license from the official website. But if you are neither of the 2 above, you can only use the software for 30 days for free and you will be charged later. 
+ The tutorial cost you about **40 minutes to go through**, however, we also need to wait for our computers to complete the rendering of the animation. So, depending on your specs, extra hours may be needed to complete the rendering. Feel free to take a nap.

Related features we applied
---------------------------

3ds Max is one of the most popular computer graphics programs for model design, animations, and digital images. Despite its other fancy and marvelous features that create dazzling effects, the functions we are applying are simple and efficient. 

+ **Max script**, the built-in scripting language for 3ds Max, is designed to complement 3ds Max, and the syntax is simple enough for non-programmers to use. 
+ **Auto Key Mode animation**, allows the user to animate the position, rotation, and scale of an object using auto-created keyframes.
+ **Set Key mode animation**, allows you to create keys for selected objects individual tracks using a combination of the Set Keys button, which has more flexibility than Auto Key Mode. 

Some basic modeling functions are also used to create a frame around the object to make the boundaries more obvious, and it is up to you to decide whether to have it or not. Please don’t be confused by all the definitions above, all of them will be explained in detail in the following parts. If you are still confused after go through the tutorial or, if something you want to achieve is not included, please go to the `Autodesk Knowledge Network <https://knowledge.autodesk.com/>`_ for more tutorials and information. 
