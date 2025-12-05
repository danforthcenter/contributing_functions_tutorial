## Analyze the Size and Shape Characteristics of Objects

Size and shape analysis outputs numeric properties for individual plants, seeds, leaves, etc.
 
**littlecv.analyze.size**(*img, mask, label="littlecv_test", plot=True*)

**returns** analysis_image

- **Parameters:**
    - img - numpy.ndarray, RGB or grayscale image data for plotting.
    - mask - numpy.ndarray, binary mask of object.
    - label - str, label for outputs
	- plot - Logical, should a debug image be printed? Defaults to True.
- **Context:**
    - Used to output size and shape characteristics of individual objects (labeled regions). 
    - About the analysis image: We draw some of the measured shape characteristics on the input `img`. The height, width,
    longest path, convex hull, and centroid are drawn in magenta. The edges of the object is drawn in blue.
- **Output data stored:** Data ('area', 'convex_hull_area', 'solidity', 'perimeter', 'width', 'height', 'longest_path',
'center_of_mass, 'convex_hull_vertices', 'object_in_frame', 'ellipse_center', 'ellipse_major_axis', 'ellipse_minor_axis',
'ellipse_angle', 'ellipse_eccentricity', 'total_edge_length') are returned as an Outputs class object, which is basically a dictionary.


```python

from littlecv import littlecv as lcv

# Characterize object shapes
outputs, analysis_image = lcv.size(img=img, mask=mask)

```

**Source Code:** [Here](https://github.com/danforthcenter/contributing_functions_tutorial/blob/main/littlecv/littlecv/analyze_size.py)
