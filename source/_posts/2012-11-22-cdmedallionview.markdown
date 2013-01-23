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

Today I “released” a small OS X user interface component called [CDMedallionView](https://github.com/rastersize/CDMedallionView). It is a subclass of `NSImageView` which has been styled to look like the image view on the login screen of OS X Lion and Mountain Lion

<img src="http://cloud.github.com/downloads/rastersize/CDMedallionView/CDMedallionView@2x.png" alt="Screenshot of the test app showing the medallion view in three different sizes" width="408px" height="336px" class="center no-border">

It should work on OS X 10.6 and up and it supports retina screens. To build the source you need ARC (must at least be enabled for the `CDMedallionView.m` file). 

## Using the Class
As `CDMedallionView` is a subclass of `NSImageView` you can use it as you would use an `NSImageView` instance. For example in code;

    CDMedallionView *medallionImageView = [[CDMedallionView] alloc] init];
    medallionImageView.frame = NSMakeRect(0.f, 0.f, 60.f, 60.f);
    medallionImageView.image = /* some NSImage instance */; 
    medallionImageView.borderWidth = 2.f; // Default is 4.0.
    
    [self.view addSubview:medallionImageView];
    
The class can also used via interface builder, drag out an `NSImageView` and using the “Identity” inspector (⌘+⌥+3) set the class to `CDMedallionView`. You can then configure it as you please using the other inspector panels. To change the shine, shadow and border width and color create an outlet to the view and then set those in code.

## Getting the Code
You can get the component from the [GitHub project _rastersize/CDMedallionView_](https://github.com/rastersize/CDMedallionView) where you can also create issues and pull requests if you find any problems or opportunity to improve. The code is available under the _MIT license_. See [the license file](https://github.com/rastersize/CDMedallionView/blob/master/LICENSE) for more information.
