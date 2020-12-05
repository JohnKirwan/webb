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

### Pathtrackr

Pathtrackr is an R package for tracking animals. It can be run in any OS environment and requires ffmpeg, which must also be installed. Footage of a trial is accepted as a directory of still images. A separate function can build this directory from a video file.



### trackR


