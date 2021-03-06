---
title: "More Examples"
date: 2017-10-09T18:04:54+02:00
draft: false
---

GoCV comes with various useful command line utilities, that are also examples of how to use the package.

## Captest

Tests to verify you can capture video from a connected webcam.

https://github.com/hybridgroup/gocv/blob/master/cmd/captest/main.go

## Capwindow

Capture video from a connected webcam and display the video in a Window.

https://github.com/hybridgroup/gocv/blob/master/cmd/capwindow/main.go

## Faceblur

Captures video from a connected camera, then uses the CascadeClassifier to detect faces, blurs them using a Gaussian blur, then displays the blurred video in a window.

https://github.com/hybridgroup/gocv/blob/master/cmd/faceblur/main.go

## Facedetect

Captures video from a connected camera, then uses the CascadeClassifier to detect faces, and draw a rectangle around each of them, before displaying them within a Window

https://github.com/hybridgroup/gocv/blob/master/cmd/facedetect/main.go

## MJPEG-Streamer

Opens a video capture device, then streams MJPEG from it that you can view in any browser.

https://github.com/hybridgroup/gocv/blob/master/cmd/mjpeg-streamer/main.go

## Saveimage

Capture a single frame from a connected webcam, then save it to an image file on disk.

https://github.com/hybridgroup/gocv/blob/master/cmd/saveimage/main.go

## Savevideo

Capture video from a connected camera, and save 100 frames worth to a video file on disk.

https://github.com/hybridgroup/gocv/blob/master/cmd/savevideo/main.go

## Showimage

Open an image file from disk, then display it in a window.

https://github.com/hybridgroup/gocv/blob/master/cmd/showimage/main.go

## Version

Displays the current version of OpenCV that is being used by GoCV.

https://github.com/hybridgroup/gocv/blob/master/cmd/version/main.go
