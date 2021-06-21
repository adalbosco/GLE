# GLE
GLE - Graphics Layout Engine

GLE (Graphics Layout Engine) is a graphics scripting language designed for creating publication quality graphs, plots, diagrams, figures and slides. GLE supports various graph types (function plots, histograms, bar graphs, scatter plots, contour lines, color maps, surface plots, ...) through a simple but flexible set of graphing commands. More complex output can be created by relying on GLE's scripting language, which is full featured with subroutines, variables, and logic control. GLE relies on LaTeX for text output and supports mathematical formulea in graphs and figures. GLE's output formats include EPS, PS, PDF, JPEG, and PNG.

This repo contains the source code to build the executables for the GLE package.  The manul, samples and library of gle routines are (will be) put in separate repositories eventually.  

## Building with CMAKE

GLE can be build on Windows, Mac and Linux using cmake.

Libraries needed to build GLE are

* boost
* libtiff
* libpng
* zlib
* pixman
* cairo
* jpeg
* Qt5 (for GUI)

Cmake uses find_package or find_library to resolve the paths for these libraries.  These variables must be set in your environment or passed to cmake if not set cmake will look for them in the system specific locations.  For more information consult cmake documentation on find_package.  

* ZLIB_ROOT
* JPEG_ROOT
* TIFF_ROOT
* PNG_ROOT
* CAIRO_ROOT
* PIXMAN_ROOT
* GHOSTPDL_ROOT
* Qt5_DIR

### Building on linux or OSX

	cmake -S src -B build
	cd build ; make

to install gle on you machine after building

	cd build ; make install

### Building on windows with Visual Studio as 64 bit executable

	cmake -S src -B build -A x64 -T host=x64
	cmake --build build

To install gle on your machine afterbuilding

	cmake -P build/cmake_install.cmake

### options that control the build

 * CMAKE_INSTALL_PREFIX - set this to a different install location than the default on your system
 * USE_STATIC_RUNTIME - set this ON to build against Visual Studio static runtimes /MT instead of /MD.  You must also set Boost_USE_STATIC_RUNTIME=ON and have all other libraries build with /MT as well

### Creating packages with cpack

cpack can be utilized to create distributable pacakges.  These pacakges shdoul be considered preliminary and experimental at this time since the manual and library of GLE routines are not included and thus GLE will not be complete.


	cd build & cpack -G "WIX;NSIS;ZIP"

	or on linux

	cd build & cpack -G "DEB;ZIP"


