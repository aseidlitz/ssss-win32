Installing GMP

GMP has an autoconf/automake/libtool based configuration system. On a Unix-like system a basic build can be done with

     ./configure
     make
     

Some self-tests can be run with

     make check
     

And you can install (under /usr/local by default) with

     make install
     



Microsoft Windows
    On systems *-*-cygwin*, *-*-mingw* and *-*-pw32* by default GMP builds only a static library, but a DLL can be built instead using

          ./configure --disable-static --enable-shared
          

    Static and DLL libraries can't both be built, since certain export directives in gmp.h must be different. --enable-cxx cannot be used when building a DLL, since libtool doesn't currently support C++ DLLs. This might change in the future.
Microsoft C
    A MINGW DLL build of GMP can be used with Microsoft C. Libtool doesn't install .lib and .exp files, but they can be created with the following commands, where /my/inst/dir is the install directory (with a lib subdirectory).

          lib /machine:IX86 /def:.libs/libgmp-3.dll-def
          cp libgmp-3.lib /my/inst/dir/lib
          cp .libs/libgmp-3.dll-exp /my/inst/dir/lib/libgmp-3.exp
          

    MINGW uses the C runtime library msvcrt.dll for I/O, so applications wanting to use the GMP I/O routines must be compiled with cl /MD to do the same. If one of the other C runtime library choices provided by MS C is desired then the suggestion is to use the GMP string functions and confine I/O to the application. 


---------------

Compiles and passes tests cleanly

---------------

Libraries have been installed in:
   /usr/local/lib
Include file in /usr/local/include/gmp.h

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.

try /configure --disable-shared --enable-static

-------------

ssss
-------------

gcc -W -Wall -O2 -I/usr/local/include -L/usr/local/lib -lgmp -o ssss-split ssss.c


