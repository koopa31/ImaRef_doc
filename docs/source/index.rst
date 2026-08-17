Welcome to Napari ImaRef's documentation!
===================================

**Napari ImaRef** is a Napari plugin designed to standardize the orientation of 3D biological specimens by defining a reproducible orthonormal reference frame. The method relies on fitting an ellipsoid from a set of manually placed anatomical landmarks. The center and principal axes of the fitted ellipsoid are then used to define the reference frame and consistently align specimens across datasets.

The approach is particularly suited to biological structures with identifiable anteroposterior (AP) and dorsoventral (DV) axes and a geometry that can be approximated by an ellipsoid through landmark placement. ImaRef has currently been validated on the **olfactory system of zebrafish embryos** and on the **whole Drosophila embryo**, demonstrating its applicability to biological structures at different spatial scales and across distinct model organisms.

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
