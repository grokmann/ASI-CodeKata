# What I Learned from [Kata05: Bloom Filters](http://codekata.com/kata/kata05-bloom-filters/)
By [Mike Mann](https://www.twitter.com/grokmike)

## Understanding the problem
I had not heard of Bloom filters and I haven't really worked with hashes beyond simple md5 checksums of downloads. [PragDave](https://www.twitter.com/grokmike) posted a [link to a description of Bloom filters](http://pages.cs.wisc.edu/~cao/papers/summary-cache/node8.html), but it wasn't as good as ["Bloom Filters by Example"](http://billmill.org/bloomfilter-tutorial/). Based on that, I decided to use the murmur hash algorithm.

Still working with Racket, I looked for an existing package, but none existed. I figured I would have to link to a C implementation, and found a [jrslepak's Racket FFI binding for MurmurHash3 on Github](https://github.com/jrslepak/murmur3). It included a makefile, but Windows' nmake could not read it. I decided not to try to edit the makefile for nmake. That left cygwin or mingw to build the files.

I thought I had cygwin installed, and I did, but on my work  machine, and not on my personal machine. I searched for gcc using the [where command](http://stackoverflow.com/a/304447/249411), and found it had been added in "\Haskell Platform\2014.2.0.0\mingw\bin\". Looking in that folder, I found mingw32-make, which I ran to create MurmurHash3.so.