April tags for Perimetry
24-DEC-2015

Authors - Darpan Sanghavi, Sujeath Pareddy, Tejaswi Kasarla, Dhruv Joshi

Srujana - Center for Innovation, LV Prasad Eye Institute, Hyderabad

We are making use of april tags for the purposes of detecting head movement and position relative to a single camera observational unit for our pediatric perimetry device. All due credits to the original authors. We are using this code as-is for the most part. Any significant changes shall be mentioned in commits and in this README.

------------------------------------------------------
Installation Procedure:

install required dependancies in linux(Tested Ubuntu 15.04) by 

`sudo apt-get install subversion cmake libopencv-dev libeigen3-dev libv4l-dev`

and on Mac by

`sudo port install pkgconfig opencv eigen3`

The AprilTags library uses the pods build system in connection with cmake. Compile with

`cd apriltags`

`make`

After compiling, run the example program

`./build/bin/apriltags_demo`

which detects AprilTags visible in laptop or webcam images and marks any tags in the live image. See examples/apriltags_demo.cpp for the source code.

------------------------------------------------------
AprilTags library

Detect April tags (2D bar codes) in images; reports unique ID of each
detection, and optionally its position and orientation relative to a
calibrated camera.

See examples/apriltags_demo.cpp for a simple example that detects
April tags (see tags/pdf/tag36h11.pdf) in laptop or webcam images and
marks any tags in the live image.

Ubuntu dependencies:
sudo apt-get install subversion cmake libopencv-dev libeigen3-dev libv4l-dev

Mac dependencies:
sudo port install pkgconfig opencv eigen3

Uses the pods build system in connection with cmake, see:
http://sourceforge.net/p/pods/

Michael Kaess
October 2012

----------------------------

AprilTags were developed by Professor Edwin Olson of the University of
Michigan.  His Java implementation is available on this web site:
  http://april.eecs.umich.edu.

Olson's Java code was ported to C++ and integrated into the Tekkotsu
framework by Jeffrey Boyland and David Touretzky.

See this Tekkotsu wiki article for additional links and references:
  http://wiki.tekkotsu.org/index.php/AprilTags

----------------------------

This C++ code was further modified by
Michael Kaess (kaess@mit.edu) and Hordur Johannson (hordurj@mit.edu)
and the code has been released under the LGPL 2.1 license.

- converted to standalone library
- added stable homography recovery using OpenCV
- robust tag code table that does not require a terminating 0
  (omission results in false positives by illegal codes being accepted)
- changed example tags to agree with Ed Olson's Java version and added
  all his other tag families
- added principal point as parameter as in original code - essential
  for homography
- added some debugging code (visualization using OpenCV to show
  intermediate detection steps)
- added fast approximation of arctan2 from Ed's original Java code
- using interpolation instead of homography in Quad: requires less
  homography computations and provides a small improvement in correct
  detections

todo:
- significant speedup could be achieved by performing image operations
  using OpenCV (Gaussian filter, but also operations in
  TagDetector.cc)
- replacing arctan2 by precomputed lookup table
- converting matrix operations to Eigen (mostly for simplifying code,
  maybe some speedup)
