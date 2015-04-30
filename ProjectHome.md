# Use "Protocol Buffers" serialization from your .NET code #

## Introduction ##

**protocol buffers** is the name of the binary serialization format used by Google for much of their data communications. It is designed to be:

  * small in size - efficient data storage (far smaller than xml)
  * cheap to process - both at the client and server
  * platform independent - portable between different programming architectures
  * extensible - to add new data to old messages

**protobuf-net** is a .NET implementation of this, allowing you to serialize your .NET objects efficiently and easily. It is compatible with most of the .NET family, including .NET 2.0/3.0/3.5, .NET CF 2.0/3.5, Mono 2.x, Silverlight 2, etc.

## The short version ##

(see also the [old home page](http://code.google.com/p/protobuf-net/wiki/HomePagePre2))

Serialization is a pain. protobuf-net is designed to be easily used on **_your existing code_** with minimal changes (of from an optional .proto schema), enabling fast and portable binary serialization on a wide range of .NET platforms.

Rather than being "a protocol buffers implementation that happens to be on .NET", it is a ".NET serializer that happens to use protocol buffers" - the emphasis is on being familiar to .NET users (for example, working on mutable, code-first classes if you want). I've also added a range of commonly requested features _beyond_ the regular protobuf design, to help meet the every-day demands of .NET programmers (inheritance, reference-tracking, etc).

Usage is very simple; at the most basic level, simply read from a stream or write to a stream; see [Getting Started](http://code.google.com/p/protobuf-net/wiki/GettingStarted):

```
// write to a file
Serializer.Serialize(outputStream, person);

...

// read from a file
var person = Serializer.Deserialize<Person>(inputStream);
```

Oh, and it is very fast; both in CPU and in bandwidth.

There is some VS tooling if you want to work from .proto files in visual studio, but you _don't need that_ - you can just write a class, tell the serializer how to work with it (most commonly by adding a few attributes, but that is up to you), and serialize away.

## "v2" released ##

"v2" is a major overhaul to the core engine to allow much greater flexibility, and avoid a number of problems with over-use of generics. It is wire-compatible with your existing data, and the old API still exists. Simply: the library is much cleaner and leaner, and is much more versatile for onwards development. In particular v2 allows:

  * allow use on more platforms (iOS, WP7, Mono for Android, WinRT, etc)
  * allow use without attributes if you wish
  * allow pre-generation of a serialization assembly, to remove all reflection at runtime
  * and generally: just more features

# Author #
The .proto serialization format is a credit to Google's ingenuity.

This specific .NET implementation is designed and written by [Marc Gravell](mailto:marc.gravell@gmail.com), developer for [Stack Exchange / Stack Overflow](http://stackexchange.com).

Credit for various compatibility issues (mono/Silverlight) goes to M. David Peterson.

Visual Basic stylesheet contributed by Michael Thaler and Rüdiger Klaehn.

Initial code for the Visual Studio "Custom Tool" by Shaun Cooley.

Thanks also to Michael Giagnocavo, for numerous good ideas from real usage.