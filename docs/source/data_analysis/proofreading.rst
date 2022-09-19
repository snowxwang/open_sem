Data Proofreading
=================

Contributor: Haishan Zhang

.. autosummary::
   :toctree: generated

Here we are sharing our proofreading pipeline to show how this procedure can be standardized. 

Preparations & File Management
------------------------------

- Always work on your own file
    + Do not make changes on the original .vsseg file or other people’s versions
    + Before working on a new cell, make sure to duplicate the source file and store it in your designated folder (preferably a local folder)

- Naming convention: 
    + Your folder’s name: Yourname
    + Cell’s folder’s name: pyr#_Yourname 
    + Version’s name: pyr#_ddmmyy_Yourname 

- Save your work regularly (e.g. every 2-3 hours). Save your segmentation as a new version at the beginning of each day and make sure to save it at the end of the day.

- So, a good working folder will look like this:


VAST Tutorial
-------------

1. Open the files you need:
    + .vsvi: the image volume
    + .vsvi that says “seg” or something similar”: the auto segmentation
    + .vsseg: the manual segmentation you will be working on
    + Open these files by dragging the file to the software or click file->open (recent) image volume/open (recent) segmentation

2. Make sure that the auto segmentation is not visible. Toggle the alpha value to adjust the transparency of the segmentation (the teal part in Picture 1) to your preference. The recommended alpha value is between 10 - 40 so that your segmentation layer is visible, but not blurring details such as cell membrane or vesicles. 

3. Select the “draw segment mode” (the pencil icon). If you want to navigate under this mode, press ctrl while moving your cursor. 

4. Turn on z-scrolling. This allows you to draw continuously through multiple pages as you set your pen on one point and flip forward or backward.

5. Enable masking. Choose your auto segmentation file as the source. Choose “auto pick source color” as the method.

6. Go to the starting point by right clicking your “segment color” (Usually it’s the color other than the background, with the name being your cell#). Select “go to anchor point”.
    + Note that when your mouse stays at these floating windows (i.e. the windows mentioned in D, E, F), any changes such as moving cursors or pressing keys will apply to contents in the windows. If the software is not functioning as you wish, come back to check whether any change is accidentally made. For instance, if you pressed up/down while the cursor is on the “segment colors” window, you might now be on the background layer, where you cannot edit anything. 
    + If no anchor point is set or it was set at a wrong place, find the cell body and click “set anchor point”. Regarding how to find the cell body, ask someone to help if you cannot ;)

7. Press a or up to flip forward, in which case the z coordinate becomes smaller. Press z or down to flip backward, in which case the z coordinate becomes bigger.

.. note::

   Note that forward/backward, smaller/bigger are just a relative way to talk about how we navigate through the pages. To get a better understanding of how you are traveling through a cell, you will need to open the neuroglancer and explore what coordinates mean in the 3d model.

8. Use your mouse scroll to zoom in or out. **Always work on mip level 1 or 0**.


WACOM Tutorial
--------------

- Press the lower button for “erase” mode
- Press the upper button to adjust the pen diam
- If you need to adjust the pen’s tip feel, mapping, and other properties, go to wacom’s app (just search “wacom”).


Tracing
-------

Our main goals are:

- Sometimes other axons or dendrites are identified and auto-segmented as part of the target dendrite due to membrane break. **Erase** them whenever you see them.
- If there are vast numbers of pages missing segmentation or the segmentation is too coarse, having pixel-like edges, **report** them to your supervisor. 
- **Find** out the missing spines. See more below.


Though the three elements in picture 3 are ubiquitous to all synapses, the shape of each spine (including head and neck) looks very different on EM images depending on on which panel you are observing it. You will get better at identifying spines and painting them across pages with some practice.


**Some pro tips**:

- When first working with EM images, take some time to navigate back and forth and visualize: 
    + Given a certain page, can you project the segmentation onto the 3d structure? Illustrations that may help you to conceive:
    + When navigating in one direction, can you relate the 2D-shape change to the 3D-structure change?

- Always note down the coordination where you have questions. **When in doubt, ask!**
- Remember that in most cases, protrusions mean active spines. Do not give up until you see the synapse. However, there are cases where protrusions end without forming a head and a synapse. If you have just started to proofread, ask your supervisor if a questionable tail really ends without the head (chances are that you just overlooked the head ;)
- When you encounter a longitudinal section, the segmentation (i.e., the colored shape) can be very long and big. In order to keep track of everything, remember to first zoom out to get a rough idea about how the dendrite is going (in both a&z directions). Then split the whole shape into several parts and track each part individually. 
- If in your image, there are too many synapses popping up and dwindling down, do not forget to go back and forth to check 1-2 times after you think you’ve finished everything. You never really finish all the spines! 
- Common mistake for newbies: on 2D images, a synapse will disappear like dissolving in the darkness. Sometimes a similar-sized oval will appear immediately, this is someone else. Do not fill this in as it may lead you to merge your dendrite with a random passer-by.
- Once again, **when in doubt, ask!**


Note Taking
-----------

If you look at the pyramidal cells (and other types of neurons), you will find that neurites always branch into two at any branch point. 

On our images, this feature looks like the following images:

If the branches go in x/y direction, you will find (on 2D image) one shape split into two smaller shapes when going in either a/z direction.

However, if the branching happens in z direction (i.e. the direction along which you are traveling through the neuron), you will find one sub-branch goes in the original a/z direction, and the other in the opposite z/a direction. Under this circumstance, you will never see both sub-branches on the same page.

With that said, our note taking method is:

- Mark the beginning of a selected dendrite as integrals (For instance, 1)

- Whenever at a branching point:
    + Mark down the page where it is about to branch
    + Create new label as, for instance, 1.1 and 1.2
    + Mark down the starting point of 1.1 and 1.2 immediately

- Repeat until the dendrite ends
    + In most cases, dendrites end in two ways: it reaches page 0/the last page (i.e. the z border); it goes out of the image (i.e. the x/y border).
    + Very very rarely, a dendrite might end in the middle for some reason. Always consult your supervisor before marking it as a special ending.

.. note::

   Remember to copy and paste coordinates after you place the target segmentation in the middle. In other words, make sure the crosshair is amid your segmentation. Since there are usually multiple segmentation shapes on one page (such as in picture 1, 8, and 10), this allows you to quickly pinpoint what your notes refer to. 

.. note::

   There’s no requirement on how detailed your notes should be. The bottom line is you take down every branching point (recall: the starting point + the beginning points of the two sub-branches). However, it is suggested to:

   - Leave a mark whenever a dendrite branch ends. Since you have a beginning point on record, chances are that you take it as a finished branch and skip it. An ending mark is thus really helpful. 
   - Take down some midway coordinates. Sometimes dendrites grow spines rampantly but do not branch for a long time. This can drive you nuts. Take down some midway coordinates when you (and the dendrite!) are sober. This helps you to step back and begin again when you get lost in the jungle of spines. 
   - Sometimes the dendrite zigzags in the z direction, which means you need to go back and forth frequently. Make a note at the turning point and label a/z, this helps you to step back and begin again whenever needed.


Without saying, it is also important to take notes of any interesting findings. After you finish proofreading a neuron, please store the note in the corresponding folder.



Voila! Now you can open VAST and try proofreading :)
