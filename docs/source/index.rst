Welcome to Napari ImaRef's documentation!
===================================

**Napari ImaRef** is a Napari plugin dedicated to stereotyping the olfactory system of zebrafish
embryos imaged in 3D, by creating a reproducible orthonormal reference frame. The method relies on ellipsoid fitting through the manual placement of well-defined points within the embryo. The center and axes of the ellipsoid define an orthonormal reference frame.

The aim of the project is to rapidly create a reference frame in different embryos to get rid of the orientation
differences during acquisition and make analyses (tracking, counting, orientation characterization) comparable.

Check out the :doc:`usage` section for further information, including
how to :doc:`install <installation>` the project.

.. note::

   This project is under active development and funded by Julie Batut's team at the Centre for Integrative biology in Toulouse.

   If you manage to apply this method to other sample types, we’d love to hear about it! And if you’re considering adapting it to different biological systems but feel that a few modifications might be necessary, don’t hesitate to reach out.

.. figure:: https://raw.githubusercontent.com/koopa31/ImaRef_doc/main/docs/images/ecran_accueil.png
    :width: 100 %

Contents
--------

.. toctree::

   installation
   usage
