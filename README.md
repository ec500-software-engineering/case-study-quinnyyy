# Case Study: OpenCV  
## Technology and Platform used for Development  
### What coding languages are used? Do you think the same languages would be used if the project was started today? What languages would you use for the project if starting it today?  

OpenCV is built in C++. C++ is a good choice for OpenCV because as a computer vision and machine learning library it demands high performance, and C++ is one of the best performant high level languages. OpenCV was originally started in 1999 which also explains why it was built in C++. I think that if the project was restarted today they would probably place more focus on Python because Python has become one of the leading languages in computer vision(?) and machine learning since 1999. Currently OpenCV does support Python and other languages but more of their focus seems to be on C++. For my case study I used the Python library for OpenCV.

### What build system is used (e.g. Bazel, CMake, Meson)? What build tools / environment are needed to build (e.g. does it require Visual Studio or just GCC or ?)  

OpenCV uses CMake as its build system.

### What frameworks / libraries are used in the project? At least one of these projects don’t use any external libraries or explicit threading, yet is noted for being the fastest in its category--in that case, what intrinsic language techniques is it using to get this speed.

![](dependencies.png)

OpenCV takes advantage of many third party libraries. A lot of these libraries just make it easier to work with images. OpenCV also has a lot of optional third party libraries such as FFMPEG that are required for some features, but if you do not want to use these features you don't need these libraries.

## Testing: describe unit/integration/module tests and the test framework
For unit testing, OpenCV uses the Google Test framework. The same tests are done on all supported platforms i.e. Windows, MacOS, Linux, Android and the majority of testing is done using the C++ API. OpenCV runs two types of tests: accuracy tests and performance tests. Accuracy tests run OpenCV functions with different parameters and check it against a reference output. These tests are to ensure that OpenCV is consistent across platforms with different hardware and software. Performance tests ensure that the software can handle a specific workload. 
### How are they ensuring the testing is meaningful? Do they have code coverage metrics for example?
I think that the Google Test framework includes code coverage in their testing so OpenCV probably uses this.
### What CI platform(s) are they using (e.g. Travis-CI, AppVeyor)?
OpenCV uses their own system for Continuous Integration called [BuildBot](http://pullrequest.opencv.org).  
It monitors the active pull requests by keeping a log of the title and description, author, and the passing and failing builds. It keeps track of which platforms are passing and which are failing.  
![](buildbot.png)
### What computing platform combinations are tested on their CI? E.g. Windows 10, Cygwin, Linux, Mac, GCC, Clang
Linux x64, Linux OpenCL, Linux AVX2, Win64, Win64 OpenCL, Mac, Mac OpenCL, Android armeabi-v7a, Linux x64 debug, Docs, iOS, Linux32, Win32, Win64 MSVS2017, Win64 MSVS2017 OpenCL, ARMv7, ARMv8, Android pack, Custom
## Software architecture in your own words, including:
OpenCV has a modular structure, consisting of many core modules. These modules are:  
Core functionality - this module defines basic data structures for use in computer vision applications, such as dense, multi-dimensional arrays. It also contains basic functions that are used by all other modules, such as swap and overloaded operators. It also contains enumerations and typedefs used by other modules.  
Image processing - this is an image processing module that includes algorithms for image filtering, geometrical image transformations such as resizing and changing perspective, and color transformations.  
Video - this modules contains algorithms for video analysis, such as motion estimation, background subtraction, and object tracking.  
calib3d - module containing geometry algorithms, such as camera calibration (single and stereo), and pose estimation. 3d reconstruction  
features2d - 2d feature detectors  
objdetect - detection of objects of predefined classes i.e. faces, eyes, etc.  
highgui - GUI  
Video I/O - IO for video capturing  
gpu - GPU-accelerated algorithms  
All these modules are bundled together in the core OpenCV library and organized using Object Oriented paradigms.  

### How would you add / edit functionality if you wanted to? How would one use this project from external projects, or is it only usable as a standalone program?
You could add / edit functionality by cloning the repository from GitHub. You could then modify the corresponding module to add the desired functinoality. OpenCV is a library that you can use in extrenal projects. So if you wanted to use OpenCV in a C++ application you would have to include the OpenCV header file. If you wanted to use OpenCV in a Python application you can import the Python library.  

### Please make diagrams as appropriate for your explanation
![](https://www.researchgate.net/profile/Saraju_Mohanty/publication/298799917/figure/fig17/AS:668711245606920@1536444593289/OpenCV-software-architecture.png)
Source: https://www.researchgate.net/figure/OpenCV-software-architecture_fig17_298799917  

### How are separation of concerns and information hiding handled?
These are handled by the architecture design choices. As mentioned earlier, each concern has a module dedicated to it. Information hiding is done using the object oriented paradigm, so relevant information is only available within the class/module.  

### Does the project lean more towards object oriented or functional components
The project leans more towards object oriented components. Each module is analogous to an object, and that object contains all of the CV/Video Processing/Image processing etc. algorithms.

## Analyze two defects in the project--e.g. open GitHub issue, support request tickets or feature request for the project
One issue that I had with the project was the `cv2.destroyAllWindows()` function did not work for me when I was running my code in a Jupyter Notebook. After the video finished playing I would have to manually force-quit the playback window, which would cause my kernel to die. 

One defect posted as a [GitHub Issue](https://github.com/opencv/opencv/issues/5150) is that the Python package crashes when used with the multiprocessing package on OSX. 
### Does the issue require an architecture change, or is it just adding a new function or?
The issue is just a matter of fixing some bug and adding support for more configurations.  

## Demonstration Application of the system
For my demonstration I made an application that will track the user's face via the webcam and identify facial landmarks i.e. mouth, nose, eyes. After identifying the eyes and mouth the application will color the eyes and mouth. A gif of the result can be seen here.  
![](output.gif)  

In my code I imported the OpenCV library for Python and used `cv2.videoCapture()` and `cv2.imshow()` to capture and display video from the user. I used a different computer vision library, `dlib`, to do create and train a model for face and facial landmark detection. To draw the eyes and mouth effects, I used `PIL`, an image processing library.
