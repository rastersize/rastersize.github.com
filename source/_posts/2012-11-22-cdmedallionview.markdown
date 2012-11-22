---
layout: post
title: "CDMedallionView"
date: 2012-11-22 16:08
comments: true
categories:
- Development
- Objective-C
- Source
- View
- OS X
---

I “released” a small OS X component today called [CDMedallionView](https://github.com/rastersize/CDMedallionView). It is a subclass of `NSImageView` which has been styled to look like the image view on the login screen of OS X Lion (and newer).

<img src="http://cloud.github.com/downloads/rastersize/CDMedallionView/CDMedallionView@2x.png" alt="Screenshot of the test app showing the medallion view in three different sizes" width="408px" height="336px" class="center no-border">

It should work on OS X 10.6 and up and it supports retina screens. To build the source you need ARC (must at least be enabled for the `CDMedallionView.m` file).

You can get it from the [GitHub project rastersize/CDMedallionView](https://github.com/rastersize/CDMedallionView) where you can also create issues and pull requests if you find any problems or opportunity to improve. The code is available under the MIT license. See [the license file](https://github.com/rastersize/CDMedallionView/blob/master/LICENSE) for more information.
