---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Animal Tracking"
subtitle: "A perusal of animal tracking software"
summary: ""
authors: [John Kirwan]
tags: []
categories: []
date: 2020-11-25T13:05:08+01:00
lastmod: 2020-11-25T13:05:08+01:00
featured: false
draft: true

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

I have looked at a few animal tracking platforms, which I have summarized below. Specifically, I have been looking for one to track a single animal across the flat circular base of an arena. These software accept footage in differing ways.

## R packages

### Pathtrackr

Pathtrackr is an R package for tracking animals. It can be run in any OS environment and requires ffmpeg, which must also be installed. Footage of a trial is accepted as a directory of still images. A separate function can build this directory from a video file.

It can be installed using devtools::install_github("aharmer/pathtrackr", build_vignettes = TRUE). 


### trackR

Install using remotes::install_github("swarm-lab/trackR").

Updated a month ago. 

> trackR is an object tracker for R based on OpenCV. It provides an easy-to-use (or so we think) graphical interface allowing users to perform multi-object video tracking in a range of conditions while maintaining individual identities.

This package requires cmake and opencv as well as the R package  [RVision](https://swarm-lab.github.io/Rvision/) from the same lab. 


### trackdem

[R package](https://cran.r-project.org/package=trackdem)
[Publication](https://besjournals.onlinelibrary.wiley.com/doi/full/10.1111/2041-210X.12975)
[Tutorial](https://cran.r-project.org/web/packages/trackdem/vignettes/tutorial.pdf)
[Git Repo](https://github.com/marjoleinbruijning/trackdem)


>   The aim of trackdem is to obtain unbiased, automated estimates of population densities andbody size distributions,  using video material or image sequences as input.  It is meant to assist in evolutionary and ecological studies, which often rely on accurate estimates of population size, population structure and/or individual behaviour. The package trackdem includes a set of functions to convert a short video into an image sequence, background detection, particle identification and linking, and the training of an artifical neural network for noise filtering.

Last updated 10 months ago. 

## JAVA applets

### Tracker

Simple tracker software for image sequences, gif or video files (.mov, .avi, .mp4, .flv, .wmv, .ogg). Accepts a simple scale calibration.


## Python modules

### Tracktor

It appears to be infrequently updated.



### Ctrax

Last updated in 


### ID tracker AI

Last upate 7 months ago.

