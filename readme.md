# Contributing New Functions to PlantCV

This repository is a place for you to learn to contribute to PlantCV in one of our guided new contributor workshops. For full documentation or asynchronous learning about contributing to PlantCV please see the [contribution docs](http://plantcv.readthedocs.io/en/latest/CONTRIBUTING/), for an online version of the [littlecv docs see the datascience website](https://datasci.danforthcenter.org/littlecv/).

## Getting started

To get started you will need an environment with at least `numpy`, `cv2`, `matplotlib`, `pandas`, `python-dateutil`, and `skikit-image` Python libraries installed. We recommend installing `PlantCV` in editable mode if you have not already done so as that will be best for contributing and will install everything you need for this activity. If you are looking to contribute to PlantCV then you may already have a conda environment set up for `PlantCV` and that would work for this workshop as well, whether `PlantCV` is editable or not in that installation.

### Installing littlecv

* First, Clone this repository (`git clone https://github.com/danforthcenter/contributing_tutorial.git`). Throughout this readme we include git CLI commands but [Github Desktop](https://github.com/apps/desktop), [Git Kraken](https://www.gitkraken.com/), or Git through VSCode/other IDEs are all friendlier options and worth learning to use.
* Next, `cd` to the cloned repo (`cd contributing_tutorial`)
* Finally, with your `PlantCV` or equivalent environment active, install `littlecv` by running `pip install -e .`.

Now you will have an editable version of `littlecv` installed locally. You can check your installation by running this command, which should tell you that you'll be an author soon:

```
python -c "from littlecv import littlecv as lcv; print(lcv.__author__)"
```

## The task

In this repository there is a small Python library called `littleCV`, these are just a handful of `PlantCV` functions with some of the more complicated features removed.

There is also an iPython notebook running a simple workflow using `littleCV`. The functions that exist in `littleCV` work in this tutorial, but you'll need a new function to get what you want. In the [`contributing_tutorial`](https://github.com/danforthcenter/contributing_tutorial) activity your task was just to find an error in existing code, which is an important kind of contribution to a codebase like `PlantCV`. In this tutorial your task is to add a totally new outward facing (exported) function. The point of this task is not to do complex Python coding but to familiarize with making edits to the files that define a Python package, writing clean code to match a codebase's style requirements, and making useful docstrings. If you get stuck on the Python coding aspect of this exercise that is okay, everyone contributing to `PlantCV` has different background and experience in Python so some tasks will be easier or harder for different people, you can check the example at the bottom of this readme file for guidance.

The function that you are adding should crop an image using a top left coordinate (x, y), height of the cropped section, and width of the cropped section. Your function should be callable by a user after the standard `from littlecv import littlecv as lcv` import syntax as `lcv.crop` or something similarly named. Other than that, just make a function that crops an image and make the tests pass on github actions (note that this includes making sure that you cover your new function with tests).



#### Steps

* 1: Open a branch with your name (`git checkout -b first_last`).
* 2: Set up an image object to crop in jupyter (run `jupyter-lab` and use GUI).
* 3: Edit `littlecv` code to add your function to `littlecv` OR write your function in jupyter. Some of our team likes to prototype functions in jupyter cells first, others prefer to edit python files and restart the kernel after each set of changes. Which you choose is up to you. Either way you will eventually need a module that defines your function and to add that module to `__init__.py`.
* 4: Restart Jupyter Kernel (or run the cell with your function in it) and test your function, alternating between edits and interactive testing until you are satisfied.
* 5: Write tests for your function. In `PlantCV` this would mean a new `test_crop.py` file, but you can add it to `tests/test_littlecv.py` or make another file, that is up to you. When you are satisfied use `py.test --cov littlecv --cov-report="term-missing"`.
* 6: Write documentation for your new function (see the `docs` folder in this repo) and add the new docs page to `mkdocs.yml`.
* 7: Commit your changes (`git commit -m "your commit message here"`). This is like saving the files on your branch. How often you do this and how granular commits are is mostly up to you.
* 8: Push your changes to github (`git push origin main`). This syncs the changes you've committed to github so that other people could pull them and use them locally.
* 9: Open a Pull Request. These are a feature of Github, not of Git itself, so we'll have to do this online or through a software like Github Desktop. Go to `https://github.com/danforthcenter/contributing_functions_tutorial/tree/YOUR_BRANCH_NAME` or to [`https://github.com/danforthcenter/contributing_functions_tutorial`](https://github.com/danforthcenter/contributing_functions_tutorial) and use the branch dropdown menu to select your branch. On your branch there should be a green `Compare and pull request` button, click that and fill out the template. There is a sidebar of options for labels, assignees, reviewers, etc. In `PlantCV` you'll; use those to describe the purpose of your PR at a very high level, mark it for a certain version milestone or request certain reviewers based on who has domain expertise or last edited those files. Once you are done with the description click `create pull request`. Once the pull request is created the automated checks will run, if those pass then you are done. You might see deepsource problems that do not show up on your local tests since deepsource is more particular about code style, etc.


### The Functions

`littlecv` only has 6 exposed functions, they are:

* `readimage`: Reads an image into a numpy.ndarray. Simplified from `plantcv.plantcv.read_image`
* `rgb2gray_lab`: Converts an RGB image to grayscale with either L, A, or B channel. Simplified from `plantcv.plantcv.rgb2gray_lab`.
* `binary`: Applies a binary threshold. Simplified from `plantcv.plantcv.threshold.binary`.
* `fill`: Filters small objects. Simplified from `plantcv.plantcv.fill`.
* `size`: Calculates single value phenotypes given a mask and image. Simplified from `plantcv.analyze.size`
* `plot_image`: Plots an image. Simplified from `plantcv.plantcv.plot_image`.

There is also a minimal `Outputs` class called by `size` to store results which is based on the `plantcv.plantcv.Outputs` class.


### If you get stuck

If you get stuck with the Python coding part of this exercise then start from something like this example to familiarize with subsetting numpy arrays:

```
import numpy as np
# images are numpy arrays
# numpy arrays can have each dimension subset with a range [inclusive, exclusive)
a1 = np.array([[1,2,3,4], [5,6,7,8], [9,10,11,12]])
print(a1[0:1, 0:3]) # first "row", first, second, and third "columns". Remember Python is 0 indexed.

# many images will have at least 3 channels
a2 = np.zeros((100, 100,3))
# ":" is shorthand for "all"
a2[:,:,0] = 255
# print a small piece of this array
a2[0:2, 0:2, 0:4]
```
