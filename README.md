## NNanomsg

This is a lightweight wrapper around the <a href="http://nanomsg.org">nanomsg.org</a> C API which makes it callable from .NET languages.

It works (without recompiling) on both Windows and Linux (the latter using mono). 

So far, I have only implemented the subset of functionality that I need, however it should be relatively straight forward and not take very long to implement the rest of it (I may do this myself, at least a little more very soon).

The advantages of wrapping the C API rather than implementing it entirely in a .NET language are:
 1. It is much less work. This means that:
 2. I have written very little code in which to introduce bugs. All functionality is provided by the C implementation which should be well tested and tuned. This is an important point and it is something that worries me about using a library that offers API's in a large number of different languages - I wonder about the quality of all these implementations!

The disadvantages are:
 1. It forces .NET applications that use the library to be platform dependent. 
 2. It means you have to bugger about with C compilers / native linking which depending on your luck and level of expertise has the potential to cause headaches.
 3. I'm not sure which method is more efficient. Possibly there are GC isses related to pinned memory with this type of implementation. In my applications, I've never run into any practical problems however.


### Example

A simple C# example is included in the source distribution.


### Development Status

Partial Implementation of interface only. 

Tested against nanomsg version 0.1alpha only.

Alpha quality. 


### Building Notes

Build nanomsg.dll and/or libnanomsg.so as instructed by the nanomsg.org website and make sure they can be found by the .NET runtime when you execute your application. I tend to include these libraries in my project and have them coppied automatically into the application directory when built.

I've included a Vagrantfile that builds a VM with nanomsg and mono installed which can be used to run the test project.

You will need to set the 'Platform Target' to x86 in any project that references NNanomsg.
