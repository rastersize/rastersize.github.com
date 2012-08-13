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

`ObjectToXPC` is a small open source project I hacked together today. It simplifies the conversion between a few Objective-C classes and the "new” _XPC_ objects. The library also comes with unit tests which covers quite a few scenarios, woop woop!

So that might be cool but what is _XPC_? XPC is new technology from Apple introduced in Mac OS X 10.7 (not publically available in iOS). It allows you to separate your application in different logical parts – services. These services all run as individual processes. Furthermore, each logical part can have a unique set of sandbox privileges. For example you can have one XPC service for network based communication and another for creating a ZIP-file of some downloaded data. Thus the technology can help yoy make your application more stable and secure.


## Supported Types ##
`ObjectToXPC`supports a few basic _Objective-C_ classes and most _XPC Object_ types.

### Objective-C ###
`ObjectToXPC`will allow you to convert instances of the following Objective-C classes to and from XPC Objects;

- `NSArray` <span class="meta">_(where the elements are one of the supported)_</span>,
- `NSData`,
- `NSDate`,
- `NSDictionary` <span class="meta">_(where the elements are one of the supported, keys must either be of the NSString class or define the `-description` method)_</span>,
- `NSNull` <span class="meta">_(only in collections)_</span>,
- `NSNumber`,
- `NSString`.

If you try to convert an `NSArray` or a `NSDictionary` instance which contains an object which we can not convert (_i.e._ if the method `-XPCObject` is not implemented) the project will halt via an assertion. But only if the `DEBUG` macro has been set. Otherwise an error will only be logged to the console via `NSLog()` and program execution will continue with the object being skipped.

### XPC Objects ###
The following types of XPC Objects can be converted to and from the previously mentioned Objective-C classes (via for example `-initWithXPCObject:`);

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
You can find the project and the glory source code on the [GitHub project page](https://github.com/rastersize/ObjectToXPC). Feel free to fork, add and fix stuff which I have missed or forgotten. Feel free to send me a pull request, I will happily intergrate it (if it looks OK)! The Xcode project file currently contains one dynamic library target and one unit test target.

To use it you can either link with the library or copy the source files manually into you project. You need all the `.h` and `.m` files found in the `Source` directory in case you opt for the latter case. As the XPC API was introduced in OS X 10.7 the project requires OS X 10.7 or newer, big suprise there. This is required both for building the project (with Xcode 4.2+ and ARC turned on) as well as running it. `ObjectToXPC` will not build for, or run on, the iOS platform as XPC Services does not exist (publically) on it.

## License ##
The project is licensed under the "Simplified BSD license" (2-clause), for the exact terms please see the [LICENSE file](https://github.com/rastersize/ObjectToXPC/blob/master/LICENSE) in the repository.

## Bugs and Other Reports ##
Please file any bug reports in the [issue tracker for ObjectToXPC](https://github.com/rastersize/ObjectToXPC/issues) on GitHub or even better fix it and then send me a pull request, also via [GitHub](https://github.com/).

Have you created an application which use any of my [open source projects](https://github.com/rastersize) (including ObjectToXPC)? Please tell me about it. Not because you have to but because I would love to know! My [contact details](/about) are available on [my about page](/about). 

