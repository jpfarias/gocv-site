---
title: "Windows"
date: 2017-10-09T11:41:54+02:00
draft: false
weight: 3
---

This page has information on how to install and use GoCV on Microsoft Windows 10, 64-bit.

### Installing

Install the GoCV package:

        go get -u -d gocv.io/x/gocv

In order to use GoCV on Windows you must build and install OpenCV 3.3. First download and install MinGW-W64 and CMake, as follows.

#### MinGW-W64

Download and run the MinGW-W64 compiler installer from [https://sourceforge.net/projects/mingw-w64/?source=typ_redirect](https://sourceforge.net/projects/mingw-w64/?source=typ_redirect). Choose the options for "posix" threads, and for "seh" exceptions handling, then install to the default location `c:\Program Files\mingw-w64\x86_64-7.1.0-posix-seh-rt_v5-rev2`.

Add the `C:\Program Files\mingw-w64\x86_64-7.1.0-posix-seh-rt_v5-rev2\mingw64\bin` path to your System Path.

#### CMake 

Download and install CMake [https://cmake.org/download/](https://cmake.org/download/) to the default location. CMake installer will add CMake to your system path.

#### Download OpenCV 3.3 and OpenCV Contrib Modules

Download the source code for OpenCV's master branch from [https://github.com/opencv/opencv](https://github.com/opencv/opencv) and extract it to the directory `C:\opencv\opencv-3.3.0`

Download the source code for OpenCV Contrib master branch from [https://github.com/opencv/opencv_contrib](https://github.com/opencv/opencv_contrib) and extract it to the directory `C:\opencv\opencv_contrib-3.3.0`

Create the directory `C:\opencv\build` as the build directory.

Now launch the `cmake-gui` program, and set the "Where is the source code" to `C:\opencv\opencv-3.3.0`, and the "Where to build the binaries" to `C:\opencv3\build`.

Click on "Configure" and select "MinGW MakeFile" from the window, then click on the  "Next" button.

Click on the "Configure" button and wait for the configuration step.

Now, scroll down the list and change the following settings as follows:

- `BUILD_DOCS` should be unchecked (aka disabled).
- `BUILD_TESTS` should be unchecked (aka disabled).
- `BUILD_PERF_TESTS` should be unchecked (aka disabled).
- `ENABLE_PRECOMPILED_HEADERS` should be unchecked.
- `ENABLE_CXX11` should be checked.
- `OPENCV_EXTRA_MODULES_PATH` should be set to `C:\opencv\opencv_contrib-3.3.0\modules`

Click on the "Configure" button again, and wait for the configuration step.

Some new configuration options will have appeared. Scroll down the list and change the following settings as follows:

- `BUILD_opencv_saliency` should be unchecked (aka disabled). OpenCV Contrib's "Saliency" module is unable to build on Windows with this toolchain at this time.

Click on the "Configure" button again, and wait for the configuration step.

Once it is complete, click on the "Generate" button, and wait for it to generate your make files. 

Now run the following commands:

		cd C:\opencv\build
		mingw32-make

The build should start. It will probably take a very long time. When it is finished run:

		mingw32-make install

Last, add `C:\opencv\build\install\x64\mingw\bin` to your System Path.

You should now have OpenCV 3.3 installed on your Windows 10 machine.

### How to build/run code

In order to build/run Go code that uses this package, you will need to specify the location for the include and lib files in your GoCV installation.

One time per session, you must run these commands:

		set CGO_CPPFLAGS=-IC:\opencv\build\install\include
		set CGO_LDFLAGS=-LC:\opencv\build\install\x64\mingw\lib -lopencv_core330 -lopencv_videoio330 -lopencv_imgproc330 -lopencv_highgui330 -lopencv_imgcodecs330 -lopencv_objdetect330 -lopencv_calib3d330

Now you should be able to build or run any of the command examples:

		go run .\cmd\version\main.go

The version program should output the following:

		gocv version: 0.1.3
		opencv lib version: 3.3.0-dev
