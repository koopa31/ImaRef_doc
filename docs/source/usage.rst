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

   .. image:: _static/select_folder.png
      :alt: Select Folder

2. **Place the Points in the Image**

   - For each image, place eight points in the following order (the instructions to place the points in
    the plugin interface):
     1. The summit of the cone.
     2. The first point to define the plane.
     3. The second point to define the plane.
     4. The third point to define the plane.
     5. The fourth point to define the plane.
     6. The top of the embryo.
     7. The bottom of the embryo.
     8. A point on the base.

   .. image:: _static/place_points.png
      :alt: Place Points

3. **Calculate the Coordinates**

   - Once all eight points are placed, click on the "Calculate Coordinates" button to compute the reference frame.

   .. image:: _static/calculate_coordinates.png
      :alt: Calculate Coordinates

4. **View and Adjust the Reference Frame**

   - The plugin will display the calculated reference frame, including the origin and the unit vectors.
   - If necessary, you can adjust the reference frame by repositioning the points and recalculating the coordinates.

   .. image:: _static/view_reference_frame.png
      :alt: View Reference Frame

5. **Save the Results**

   - The plugin will save the coordinates and the reference frame data in a CSV file in the same folder as the images.

   .. image:: _static/save_results.png
      :alt: Save Results

Notes
-----

- Ensure that you place the points accurately to get a reliable reference frame.
- The plugin supports various image formats including `.png`, `.TIF`, `.tif`, and `.tiff`.


