---
layout: post
title: "Convert between XPC objects and Objective-C objects"
date: 2011-12-17 22:24
comments: true
categories:
- Development
- Source
- Objective-C
- XPC
---

`ObjectToXPC` is a small open source project I hacked together today. It simplifies the conversion of a few Objective-C classes to and from the "new” XPC objects. It also comes with unit tests for some scenarios, woop woop!

What is XPC then? XPC is new technology from Apple introduced in Mac OS X 10.7 (not available in iOS). It allows you to separate your application in different logical parts. Each which can have different privileges under the new sandboxed environment. Thus it can help make your application more stable and secure.


## Supported Types ##
### Objective-C ###
Basically it will allow you to convert instances of the following Objective-C classes;

- `NSArray` <span class="meta">_(where the elements are one of the supported)_</span>,
- `NSData`,
- `NSDate`,
- `NSDictionary` <span class="meta">_(where the elements are one of the supported, keys must either be of the NSString class or define the `-description` method)_</span>,
- `NSNull` <span class="meta">_(only in collections)_</span>,
- `NSNumber`,
- `NSString`.

If you were to try and convert an `NSArray` or a `NSDictionary` instance which contains an object which we can not convert (_i.e._ if the method `-XPCObject` is not implemented) the project will halt you via an assertion. But only if the `DEBUG` macro has been set. Otherwise an error will only be logged to the console via `NSLog()` and program execution will continue with the object being skipped.

### XPC Objects ###
The following types of XPC objects can be used to initiate instances of the previously mentioned Objective-C classes (via `-initWithXPCObject:`);

- `XPC_TYPE_ARRAY`,
- `XPC_TYPE_BOOL`,
- `XPC_TYPE_DATA` <span class="meta">_(to and from `NSNumber`)_</span>,
- `XPC_TYPE_DATE`,
- `XPC_TYPE_DICTIONARY`,
- `XPC_TYPE_DOUBLE` <span class="meta">_(to and from `NSNumber`)_</span>,
- `XPC_TYPE_INT64` <span class="meta">_(to and from `NSNumber`)_</span>,
- `XPC_TYPE_UINT64` <span class="meta">_(to and from `NSNumber`)_</span>,
- `XPC_TYPE_NULL`,
- `XPC_TYPE_STRING`.


## Get the Code ##
Find the project and the glory source code on the [GitHub project page](https://github.com/rastersize/ObjectToXPC). Feel free to fork, add and fix stuff which I have missed or forgotten. Then please send me a pull request so that I can integrate it! The Xcode project file currently contains one dynamic library target and one unit test target.

To use it you can either link with library or copy the files manually. You need all the `.h` and `.m` files in the `Source` directory in the latter case. As the XPC API was introduced in Mac OS X 10.7 the project require OS X 10.7 and newer. Both for building (with Xcode 4.2+ with ARC turned on) and running. ObjectToXPC will not build for or run on the iOS platform as XPC Services does not exist on it.

## License ##
The project is licensed under the "Simplified BSD license" (2-clause), for the exact terms please see the [LICENSE file](https://github.com/rastersize/ObjectToXPC/blob/master/LICENSE) in the repository.

## Bugs and Other Reports ##
Please file any bug reports in the [issue tracker for ObjectToXPC](https://github.com/rastersize/ObjectToXPC/issues) on GitHub or event better fix it and then send me a pull request, also on GitHub.

Have you created an application which use any of my [open source projects](https://github.com/rastersize) (including ObjectToXPC)? Please tell me about it. Not because you have to but because I would love to know! My [contact details](/about) are available on [my about page](/about). 

