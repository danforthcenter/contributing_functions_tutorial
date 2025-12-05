## Binary Threshold

Creates a binary image from a gray image based on the threshold values. 
The object target can be specified as dark or light.

**littlecv.threshold.binary**(*gray_img, threshold, object_type="light"*)

**returns** thresholded/binary image

- **Parameters:**
    - gray_img - Grayscale image data
    - threshold - Threshold value (0-255). Values lighter than this are kept.
    - plot - Logical, should a debug image be plotted? Defaults to True.
- **Context:**
    - Used to help differentiate plant and background
- **Example use:**
    - Below


```python

from littlecv import littlecv as lcv

threshold_light = lcv.threshold.binary(gray_img=gray_img, threshold=36)

```

**Source Code:** [Here](https://github.com/danforthcenter/contributing_functions_tutorial/blob/main/littlecv/littlecv/threshold_binary.py)
