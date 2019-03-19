# Case Study: OpenCV  
## Technology and Platform used for Development  
### What coding languages are used? Do you think the same languages would be used if the project was started today? What languages would you use for the project if starting it today?  

OpenCV is built in C++. C++ is a good choice for OpenCV because as a computer vision and machine learning library it demands high performance, and C++ is one of the best performant high level languages. OpenCV was originally started in 1999 which also explains why it was built in C++. I think that if the project was restarted today they would probably place more focus on Python because Python has become one of the leading languages in computer vision(?) and machine learning since 1999. Currently OpenCV does support Python but more of their focus seems to be on C++ implementation. For my case study I used the Python library for OpenCV so I will focus on that for my answers. The GitHub page can be found [here](https://github.com/skvark/opencv-python)

### What build system is used (e.g. Bazel, CMake, Meson)? What build tools / environment are needed to build (e.g. does it require Visual Studio or just GCC or ?)  

opencv-python's [project description](https://pypi.org/project/opencv-python/) says that the project is structured like a normal Python package with a standard setup.py file. The build process is as follows:

1. Checkout repositories and submodules
2. Find OpenCV version from the sources
3. Install dependencies 
4. Build OpenCV
5. Copy each '.pyd/.so' file to cv2 folder of this project and generate wheel (?)
6. Install the generated wheel
7. Test that Python can import the library and run some sanity checks
8. Use twine to upload the generated wheel to PyPI (only in release builds)

### What frameworks / libraries are used in the project? At least one of these projects don’t use any external libraries or explicit threading, yet is noted for being the fastest in its category--in that case, what intrinsic language techniques is it using to get this speed.

The only dependency for opencv-python is numpy. numpy is great when performing matrix calculations and such in python, which are needed for machine learning and computer vision applications.

## Testing: describe unit/integration/module tests and the test framework
### How are they ensuring the testing is meaningful? Do they have code coverage metrics for example?
???
### What CI platform(s) are they using (e.g. Travis-CI, AppVeyor)?
They ues both Travis-CI and AppVeyor
### What computing platform combinations are tested on their CI? E.g. Windows 10, Cygwin, Linux, Mac, GCC, Clang
They test Python versions 2.7, 3.4, 3.5, 3.6, 3.7 on Mac OSx and Linux.
## Software architecture in your own words, including:
### How would you add / edit functionality if you wanted to? How would one use this project from external projects, or is it only usable as a standalone program?

### What parts of the software are asynchronous (if any)?

### Please make diagrams as appropriate for your explanation

### How are separation of concerns and information hiding handled?

### What architectural patterns are used

### Does the project lean more towards object oriented or functional components

## Analyze two defects in the project--e.g. open GitHub issue, support request tickets or feature request for the project

### Does the issue require an architecture change, or is it just adding a new function or?

### make a patch / pull request for the project to fix problem / add feature

Track facial features and color them  
![](./output.gif)
