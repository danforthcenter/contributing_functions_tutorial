## Fill

Identifies objects and fills objects that are less than specified size

**littlecv.fill**(*bin_img, size, roi=None*)

**returns** fill_image

- **Parameters:**
    - bin_img - Binary image data
    - size - minimum object area size in pixels (integer), smaller objects will be filled
	- plot - Logical, should a debug image be plotted? Defaults to True.
  - **Context:**
    - Used to reduce image noise

```python

from littlecv import littlecv as lcv

fill_image = lcv.fill(bin_img=binary_img, size=200)

```

**Source Code:** [Here](https://github.com/danforthcenter/contributing_functions_tutorial/blob/main/littlecv/littlecv/fill.py)
