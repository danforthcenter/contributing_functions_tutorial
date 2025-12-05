## RGB to LAB

Convert image from RGB color space to LAB color space and split the channels.

**littlecv.rgb2gray_lab**(*rgb_img, channel, plot=True*)

**returns** split image (l, a, or b channel)

- **Parameters:**
    - rgb_img - RGB image data
    - channel - Split 'l' (lightness), 'a' (green-magenta), or 'b' (blue-yellow) channel
	- plot - Logical, should a debug image be printed? Defaults to True.

- **Context:**
    - Used to help differentiate plant and background

```python

from littlecv import littlecv as lcv

l_channel = lcv.rgb2gray_lab(rgb_img=rgb_img, channel='l')

```

**Source Code:** [Here](https://github.com/danforthcenter/contributing_functions_tutorial/blob/main/littlecv/littlecv/rgb2gray_lab.py)
