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


4. **Correction of z-vector deviation (optional)**

   - If the dorsal axis is not correctly aligned after ellipsoid fitting, the user can refine it by placing a few points along the dorsal side.
     A correction is then applied to ensure that z lies in the anteroposterior plane and points dorsally.

     1. Click "Add dorsal points to orient Z-vector". The viewer will switch to 2D view mode.
     2. Manually place a few points (e.g., 2 or 3) along the anteroposterior axis in the dorsal region of the embryo
     3. Click "Calculate coordinates" to recompute the frame. The Z-vector should now be properly aligned.

    .. figure:: https://raw.githubusercontent.com/koopa31/stereotyping_doc/refs/heads/main/docs/images/correct_z.gif?raw=true
       :alt: GIF

5. **Correction of x orientation (optional)**

    - Some microscopes acquire 3D stacks in reverse z-order, which can mirror the sample along the left-right axis — for example, the left placode may appear on the right.
      This affects the computed X-axis vector and can lead to inconsistent anatomical orientations between datasets. To correct this, check the "Invert X-vector direction" box after computing the coordinate system if you observe a left-right inversion. This applies the transformation x → –x, ensuring consistent anatomical orientation across microscopes.

    .. figure:: https://raw.githubusercontent.com/koopa31/stereotyping_doc/refs/heads/main/docs/images/correct_x.gif?raw=true
      :alt: GIF

6. **How can I use my newly computed frame? (optional)**

   - Once the frame and/or the ellipsoid are displayed, you can select points in the image where you want to compute coordinates in the new frame by clicking "Compute coordinates in the new reference frame".
     Once clicked, the viewer will go back to 2D view and you will then be prompted to place as many points as desired. Their positions in the new reference frame will be saved in the CSV already containing the frame coordinates
     and displayed in the terminal. If you choose not to display the ellipsoid or the frame, the next image in the folder will be loaded automatically, and the reference frame parameters will be saved (see the next section).


   .. figure:: https://raw.githubusercontent.com/koopa31/stereotyping_doc/main/docs/images/coords.gif?raw=true
      :alt: GIF


7. **Save the Results**

   - The plugin will save the coordinates of the point placed in **4.** (not mandatory) and the reference frame parameters in a CSV file
     named as the corresponding image, in the folder containing the images.


Using my new reference frame in different scenarios
------------------------------------------------

The plugin is divided into two widgets: the first one is used to set reference frames by fitting an ellipsoid, as explained in the previous sections,
and the second one allows you to utilize those newly computed frames in various scenarios you may encounter.

With this second widget you can manage those three cases:

1. **Transform manually provided points into a new reference frame**. You get a folder containing images, their reference frame coordinates in csv files and csv files named as imagename_points.csv containing points coordinates you want to transform in the new reference frame.
2. **Transform cell centroids extracted from a segmentation mask into the new reference frame**. You get a folder containing images, their segmentation masks and csv files containing their reference framer coordinates. You can compute the cell centroids coordinates in the new reference frame for each segmented image in the folder.
3. **Transform cell tracking coordinates**. You get a folder containing all time points of a 3D+t series. You already computed the reference frame at t0 and you want to compute the tracking result coordinates in the new reference frame. It is compatible from three different tracking software:

    - `TrackMate <https://imagej.net/plugins/trackmate/>`_.
    - `Mastodon <https://imagej.net/plugins/mastodon>`_/`Elephant <https://elephant-track.github.io/#/>`_
    - `Ultrack <https://github.com/royerlab/ultrack>`_

For people who would like to code or adapt those codes for  their own application, a tutorial `Jupyter Notebook <https://github.com/koopa31/napari_stereotypage/blob/main/Transform_coordinates.ipynb>`_ computing the exact same things as the second widget is available in the Github repository. You can download it and adapt it freely.

Notes
-----

- Ensure that you place the points accurately to get a reliable reference frame.
- The plugin supports various image formats including `.png`, `.TIF`, `.tif`, and `.tiff`.


