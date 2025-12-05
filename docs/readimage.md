## Read Image

Reads image into numpy ndarray and splits the path and image filename (*see note about when `mode='envi'`). Most modes of use of this function is a wrapper for the OpenCV function [imread](http://docs.opencv.org/modules/highgui/doc/reading_and_writing_images_and_video.html).

**littlecv.readimage**(*filename, plot=True*)

**returns** img, path, image filename

- **Parameters:**
    - filename - image file to be read (possibly including a path)
    - plot - Logical, should the image be plotted when read? Defaults to True.
- **Context:**
    - Reads in file to be processed
- **Notes:**
    - Simplified from `plantcv.plantcv.readimage`.

```python
from littlecv import littlecv as lcv

#read in image
img, path, img_filename = lcv.readimage(filename="home/user/images/test-image.png")

```

**Source Code:** [Here](https://github.com/danforthcenter/contributing_functions_tutorial/blob/main/littlecv/littlecv/readimage.py)
