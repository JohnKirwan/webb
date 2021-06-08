---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Object Tracking"
subtitle: "Object tracking software (for animal behavioural)"
summary: ""
authors: [John Kirwan]
tags: []
categories: []
date: 2021-04-29T13:05:08+01:00
lastmod: 2021-04-29T13:05:08+01:00 
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---

I have looked at a few automated object tracking methods, which I have summarized below, which track objects from video recordings and which are suitable for animal behavioural experiments. (Specifically, I have been looking for one to track a single animal across the flat circular base of an arena.) Some of these methods are run using an R frontend, while others use Python. Many use the cross-platform [FFMPEG](https://en.wikipedia.org/wiki/FFmpeg) or [OpenCV](https://en.wikipedia.org/wiki/OpenCV) libraries, which are separately installed. On Windows, Python may be conveniently managed using [miniconda](https://docs.conda.io/en/latest/miniconda.html). All of the methods are free for non-commercial use. An elementary understanding of R or Python (and Shell scripting) will speed things up and make you more flexible. 

Several of these methods use algorithms that learn about the tracking objects or the background and are robust to changes throughout the recording. Some can track multiple animals and aim to keep their identities separate even where they overlap or they change apparent size or shape. Before we get to them, we can consider a few pertinent details of the recordings and analysis.

### Prepare the Visual Scene

Regardless of the method you use, aspire to keep the light environment of the background as stable and homogeneous as possible throughout the recording. Avoid bright spots, shadows or reflections which might be conflated with moving objects - especially if the contrast between the object and the background is low. This will vastly simplify tracking, which may not possible to fully automate otherwise. 

If you are tracking from multiple videos (e.g. when running multiple trials of an experiment), you will want to keep everything - including the lighting conditions, the background and the relative position of the camera - as stable as possible across videos. (It is useful to fix the camera immovably in place relative to the recorded area.) This will facilitate running automated tracking in batch, with many videos sequentially using the same settings.   

You may also want at least a frame (ideally, more) in which the focal objects are absent but the background (e.g. experimental arena) is otherwise the same. This allows you to subtract the background, leaving only the information provided by the moving objects. This is not necessary for *idtracker.ai*.

It is usually possible to define a region of interest (ROI) from the pixel coordinates (often done using a GUI) within which to track, so you need not worry about moving features or changing illumination outside this region. Once again, the precise extent of this region should ideally be the same over multiple videos. 

### Before Tracking

Expect to lose time getting these methods to work, especially if you have not previously set up the requisite software (e.g. FFMPEG or OpenCV) and especially if using Windows. Unless you are lucky, you may also encounter challenges getting your video files to be read by a particular software package. 

Aim to select your preferred tracking software in advance of video recording, so that you can ensure compatibility with the output video and that test recordings can be successfully tracked.   

### Recording video

Consider using [Python with OpenCV](https://docs.opencv.org/master/dd/d43/tutorial_py_video_display.html) to record video directly from a webcam or USB camera. This handles video very flexibly, allowing you to customize it to your needs. This is particularly useful so that you can produce files of optimal resolution, size, and frame rate, and in the ideal format for your tracking pipeline.

If you subsequently need to convert video to a different format, there are variety of means of doing this which work with the various operating systems.  

## Packages

### idtracker.ai

The [idtracker.ai](https://gitlab.com/polavieja_lab/idtrackerai) package, published [here](https://www.nature.com/articles/s41592-018-0295-5?WT.feed_name=subjects_software) is a method to accurately tracking up to 100 animals. The background can be subtracted; it is estimated automatically by averaging equally spaced frames in the video.

This software includes both a GUI and terminal mode. For tracking videos in batch, the GUI mode can be used to decide the optimum parameters, and tracking can be run in using the command line. 

[//]: # (I had difficulty running this program a single animal with a somewhat changeable light field.)

### trackR

This R package requires cmake and opencv as well as the R package  [RVision](https://swarm-lab.github.io/Rvision/) from the same lab. It provides a nice [Shiny](https://shiny.rstudio.com) UI interface that takes you through the various stages of uploading, thresholding and tracking the video. It is, however, in its development stages and bugs and issues are to be expected. 

### trackdem

An [R package](https://cran.r-project.org/package=trackdem), available on [github](https://github.com/marjoleinbruijning/trackdem), which uses FFMPEG to estimate population density and body size of many moving particles or track behaviour from a sequence of images. It is published [here](https://besjournals.onlinelibrary.wiley.com/doi/full/10.1111/2041-210X.12975) and is aimed at ecology and evolution. It is updated regularly and is available in CRAN though it is still in development releases. A tutorial is available [here](https://cran.r-project.org/web/packages/trackdem/vignettes/tutorial.pdf).

### Pathtrackr

[Pathtrackr](https://github.com/aharmer/pathtrackr) is an R package for tracking animals. It can be run in any OS environment and requires FFMPEG. Footage of a trial is accepted as a directory of still images. A separate function can build this directory from a video file.  It is in development and so far cna be used to track a single animal. 

[//]: # (Pathtrackr did not work for me. It worked to spit my video into jpgs but crashed when I ran the path tracking part, irreversibly deleting the directory in the process.)

### Tracktor

[Tracktor](https://github.com/vivekhsridhar/tracktor) is Python based software using opencv, published [here](https://besjournals.onlinelibrary.wiley.com/doi/full/10.1111/2041-210X.13166). and available at this  [repo](https://github.com/vivekhsridhar/tracktor/releases/latest).

The authors suggest running it within a Conda environment using miniconda.The preferred method is also to use jupyter notebooks.  It is a multiple animal tracking program. 

### Ctrax

Ctrax, the *The Caltech Multiple Walking Fly Tracker* is a standalone GUI software package, written in Python and described [here](DOI:10.1038/nmeth.1328). It uses machine learning to track multiple objects even with changing position and orientation, and is designed with walking fruit flies in mind. It is at a mature stage of development and has seen few changes in recent years.

It accepts Fly Movie Format (.fmf) and Static Background Fly Movie Format (.sbfmf), as well as uncompressed .avi files, produced by Matlab, mencoder and VirtualDub [see here](http://ctrax.sourceforge.net/install.html#input-video-formats). 




