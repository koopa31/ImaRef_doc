Usage
=====

This plugin allows you to generate a reference frame in an image of an embryo using a series of user-defined points.
Below are the steps to use the plugin along with illustrative screenshots.

Steps to Generate a Reference Frame
-----------------------------------

1. **Image Selection**

   - Set the image selection parameters to filter and load the correct images. We assume each channel has been saved in a separate tiff file:
       - **Sample identifier**: Used to filter images that belong to the same sample (default: `_s`).
       - **Number of colors**: Define the number of colors used in your images (default: `2`).
       - **Identifiers for the color channels**:
          - **Blue channel**: Define the identifier for blue channel images (default: `CSU-405 Em 440-460`).
          - **Green channel**: Define the identifier for green channel images (default: `CSU-488 Em 510-540`).
          - **Red channel**: Define the identifier for red channel images (default: `CSU-561 Em 593LP`).

2. **Select the Folder Containing Images**

   - Open Napari and launch the plugin.
   - Click on the "Select Folder" button to choose the folder containing your embryo images. Images must be 3D and can be composed of several channels.

   .. figure:: https://raw.githubusercontent.com/koopa31/stereotyping_doc/main/docs/images/select_folder.gif?raw=true
      :alt: GIF

3. **Place the Points in the Image**

   - For each image, place at least nine points in the following order (the instructions to place the points are detailed in the plugin interface):

     1. One point in the anterior part of the embryo, which is crucial for properly defining the orientation of the y-vector.
     2. One point in the dorsal part of the embryo, which is crucial for properly defining the orientation of the z-vector.
     3. As many points as possible around the telencephalon to fit the ellipsoid. The more the better as robustness improves with an increasing number of points.
     
   .. figure:: https://raw.githubusercontent.com/koopa31/stereotyping_doc/main/docs/images/placer_points.gif?raw=true
      :alt: GIF

   Once all points are placed, click on the "Calculate Coordinates" button to compute the reference frame. To proceed to Step 4, you must display the orthonormal frame and/or the ellipsoid before clicking "Calculate Coordinates" by selecting "Show computed orthonormal axes" and "Show the computed ellipsoid."


4. **How can I use my newly computed frame? (optional)**

   - Once the frame and/or the ellipsoid are displayed, you can select points in the image where you want to compute coordinates in the new frame by clicking "Compute coordinates in the new reference frame".
    Once clicked, the viewer will go back to 2D view and you will then be prompted to place as many points as desired. Their positions in the new reference frame will be saved in the CSV already containing the frame coordinates
    and displayed in the terminal. If you choose not to display the ellipsoid or the frame, the next image in the folder will be loaded automatically, and the reference frame parameters will be saved (see the next section).


   .. figure:: https://raw.githubusercontent.com/koopa31/stereotyping_doc/main/docs/images/coords.gif?raw=true
      :alt: GIF

5. **Save the Results**

   - The plugin will save the coordinates of the point placed in **4.** (not mandatory) and the reference frame parameters in a CSV file
     named as the corresponding image, in the folder containing the images.


Using the reference frame in different scenarios
------------------------------------------------

A `Jupyter Notebook <https://github.com/koopa31/napari_stereotypage/blob/main/Transform_coordinates.ipynb>`_ is available in the Github repository. It teaches how to:

1. Transform manually provided points into a new reference frame.
2. Transform cell centroids extracted from a segmentation mask into the new reference frame.
3. Transform cell tracking coordinates from three different tracking software:

    - `TrackMate <https://imagej.net/plugins/trackmate/>`_.
    - `Mastodon <https://imagej.net/plugins/mastodon>`_/`Elephant <https://elephant-track.github.io/#/>`_
    - `Ultrack <https://github.com/royerlab/ultrack>`_


Notes
-----

- Ensure that you place the points accurately to get a reliable reference frame.
- The plugin supports various image formats including `.png`, `.TIF`, `.tif`, and `.tiff`.


