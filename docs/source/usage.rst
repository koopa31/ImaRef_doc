Usage
=====

Usage of the Embryo Stereotyping Plugin
========================================

This plugin allows you to generate a reference frame in an image of an embryo using a series of user-defined points.
Below are the steps to use the plugin along with illustrative screenshots.

Steps to Generate a Reference Frame
-----------------------------------

1. **Select the Folder Containing Images**

   - Open Napari and launch the plugin.
   - Click on the "Select Folder" button to choose the folder containing your embryo images.

   .. figure:: https://raw.githubusercontent.com/koopa31/stereotyping_doc/main/docs/images/select_folder.gif?raw=true
      :alt: GIF

2. **Place the Points in the Image**

   - For each image, place eight points in the following order (the instructions to place the points are detailed
    in the plugin interface):
     1. The summit of the cone.
     2. The first point to define the telencephalon plane.
     3. The second point to define the telencephalon plane.
     4. The third point to define the telencephalon plane.
     5. The fourth point to define the telencephalon plane.
     6. The top of the embryo (back part).
     7. The bottom of the embryo (ventral part).
     8. A point on the cone base.

   .. image:: _static/place_points.png
      :alt: Place Points

3. **Calculate the Coordinates**

   - Once all eight points are placed, click on the "Calculate Coordinates" button to compute the reference frame.
   - You can show the axes, the telencephalon plane and the cone by ticking the corresponding cases. If so, one can click
    on *compute coordinates in the new reference frame*. You will be asked to set a point and its position will be
    saved and displayed as well as the reference frame. If you decide not to show the result, the next image in the
    folder will be loaded.

   .. image:: _static/calculate_coordinates.png
      :alt: Calculate Coordinates

4. **Save the Results**

   - The plugin will save the coordinates and the reference frame data in a CSV file in the same folder as the images.

   .. image:: _static/save_results.png
      :alt: Save Results

Notes
-----

- Ensure that you place the points accurately to get a reliable reference frame.
- The plugin supports various image formats including `.png`, `.TIF`, `.tif`, and `.tiff`.


