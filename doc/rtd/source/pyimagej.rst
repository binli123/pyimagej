PyImageJ
########

PyImageJ provides a set of wrapper functions for integration between
ImageJ+ImageJ2 and Python. A major advantage of this approach is the ability to
combine ImageJ+ImageJ2 with other tools available from the Python software
ecosystem, e.g. NumPy, SciPy, scikit-image, CellProfiler, OpenCV, and ITK.

The first step when using PyImageJ is to create an ImageJ2 gateway.
This gateway can point to any official release of ImageJ2 or to a local
installation. Using the gateway, you have full access to the ImageJ2 API,
plus utility functions for translating between Python (NumPy, xarray,
pandas, etc.) and Java (ImageJ, ImageJ2, ImgLib2, etc.) structures.

Here is an example of opening an image using ImageJ2 and displaying it:

.. highlight:: python
.. code-block:: python

    # Create an ImageJ2 gateway with the newest available version of ImageJ2.
    import imagej
    ij = imagej.init()

    # Load an image.
    image_url = 'https://imagej.net/images/clown.png'
    jimage = ij.io().open(image_url)

    # Convert the image from ImageJ2 to xarray, a package that adds
    # labeled datasets to numpy (http://xarray.pydata.org/en/stable/).
    image = ij.py.from_java(jimage)

    # Display the image (backed by matplotlib).
    ij.py.show(image, cmap='gray')

.. autofunction:: imagej.init

Classes
=======

GatewayAddons
-------------
.. currentmodule:: imagej
.. autoclass:: GatewayAddons
   :members:

ImageJPython
------------
.. autoclass:: ImageJPython
    :members:

Mode
----
.. autoclass:: Mode
    :members:
    :undoc-members:

RAIOperators
------------
.. autoclass:: RAIOperators
    :members: