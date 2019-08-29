# boost-win

## Build the Boost.Build tool (b2.exe) using this command:

### Download the distribution

https://sourceforge.net/projects/boost/files/boost-binaries/1.71.0/

### Download dependencies

http://www.zlib.net/
https://sourceforge.net/projects/bzip2/

### Seeting up the building tool

```
PS C:\Users\mg\Downloads\boost_1_71_0> .\bootstrap.bat
Building Boost.Build engine

Generating Boost.Build configuration in project-config.jam for msvc...

Bootstrapping is done. To build, run:

    .\b2

To adjust configuration, edit 'project-config.jam'.
Further information:

    - Command line help:
    .\b2 --help

    - Getting started guide:
    http://boost.org/more/getting_started/windows.html

    - Boost.Build documentation:
    http://www.boost.org/build/
```

### Building Options 

```
.\b2.exe --help
Boost.Build 4.0-git

Project-specific help:

  Project has jamfile at Jamroot

Usage:

  b2 [options] [properties] [install|stage]

  Builds and installs Boost.

Targets and Related Options:

  install                 Install headers and compiled library files to the
  =======                 configured locations (below).

  --prefix=<PREFIX>       Install architecture independent files here.
                          Default: C:\Boost on Windows
                          Default: /usr/local on Unix, Linux, etc.

  --exec-prefix=<EPREFIX> Install architecture dependent files here.
                          Default: <PREFIX>

  --libdir=<LIBDIR>       Install library files here.
                          Default: <EPREFIX>/lib

  --includedir=<HDRDIR>   Install header files here.
                          Default: <PREFIX>/include

  --cmakedir=<CMAKEDIR>   Install CMake configuration files here.
                          Default: <LIBDIR>/cmake

  --no-cmake-config       Do not install CMake configuration files.

  stage                   Build and install only compiled library files to the
  =====                   stage directory.

  --stagedir=<STAGEDIR>   Install library files here
                          Default: ./stage

Other Options:

  --build-type=<type>     Build the specified pre-defined set of variations of
                          the libraries. Note, that which variants get built
                          depends on what each library supports.

                              -- minimal -- (default) Builds a minimal set of
                              variants. On Windows, these are static
                              multithreaded libraries in debug and release
                              modes, using shared runtime. On Linux, these are
                              static and shared multithreaded libraries in
                              release mode.

                              -- complete -- Build all possible variations.

  --build-dir=DIR         Build in this location instead of building within
                          the distribution tree. Recommended!

  --show-libraries        Display the list of Boost libraries that require
                          build and installation steps, and then exit.

  --layout=<layout>       Determine whether to choose library names and header
                          locations such that multiple versions of Boost or
                          multiple compilers can be used on the same system.

                              -- versioned -- Names of boost binaries include
                              the Boost version number, name and version of
                              the compiler and encoded build properties. Boost
                              headers are installed in a subdirectory of
                              <HDRDIR> whose name contains the Boost version
                              number.

                              -- tagged -- Names of boost binaries include the
                              encoded build properties such as variant and
                              threading, but do not including compiler name
                              and version, or Boost version. This option is
                              useful if you build several variants of Boost,
                              using the same compiler.

                              -- system -- Binaries names do not include the
                              Boost version number or the name and version
                              number of the compiler. Boost headers are
                              installed directly into <HDRDIR>. This option is
                              intended for system integrators building
                              distribution packages.

                          The default value is 'versioned' on Windows, and
                          'system' on Unix.

  --buildid=ID            Add the specified ID to the name of built libraries.
                          The default is to not add anything.

  --python-buildid=ID     Add the specified ID to the name of built libraries
                          that depend on Python. The default is to not add
                          anything. This ID is added in addition to --buildid.

  --help                  This message.

  --with-<library>        Build and install the specified <library>. If this
                          option is used, only libraries specified using this
                          option will be built.

  --without-<library>     Do not build, stage, or install the specified
                          <library>. By default, all libraries are built.
Properties:

  toolset=toolset         Indicate the toolset to build with.

  variant=debug|release   Select the build variant

  link=static|shared      Whether to build static or shared libraries

  threading=single|multi  Whether to build single or multithreaded binaries

  runtime-link=static|shared
                          Whether to link to static or shared C and C++
                          runtime.


General command line usage:

    b2 [options] [properties] [targets]

  Options, properties and targets can be specified in any order.

Important Options:

  * --clean Remove targets instead of building
  * -a Rebuild everything
  * -n Don't execute the commands, only print them
  * -d+2 Show commands as they are executed
  * -d0 Suppress all informational messages
  * -q Stop at first error
  * --reconfigure Rerun all configuration checks
  * --debug-configuration Diagnose configuration
  * --debug-building Report which targets are built with what properties
  * --debug-generator Diagnose generator search/execution

Further Help:

  The following options can be used to obtain additional documentation.

  * --help-options Print more obscure command line options.
  * --help-internal Boost.Build implementation details.
  * --help-doc-options Implementation details doc formatting.

...found 1 target...
PS C:\Users\mg\Downloads\boost_1_71_0> .\b2.exe --help-options
Boost.Build Usage:

  b2 [ options... ] targets...

  * -a; Build all targets, even if they are current.
  * -fx; Read 'x' as the Jamfile for building instead of searching for the
    Boost.Build system.
  * -jx; Run up to 'x' commands concurrently.
  * -n; Do not execute build commands. Instead print out the commands as they
    would be executed if building.
  * -ox; Output the used build commands to file 'x'.
  * -q; Quit as soon as a build failure is encountered. Without this option
    Boost.Jam will continue building as many targets as it can.
  * -sx=y; Sets a Jam variable 'x' to the value 'y', overriding any value that
    variable would have from the environment.
  * -tx; Rebuild the target 'x', even if it is up-to-date.
  * -v; Display the version of b2.
  * --x; Any option not explicitly handled by Boost.Build remains available to
    build scripts using the 'ARGV' variable.
  * --abbreviate-paths; Use abbreviated paths for targets.
  * --hash; Shorten target paths by using an MD5 hash.
  * -dconsole; Run the interactive debugger. Cannot be used with any other
    option.
  * -dn; Enables output of diagnostic messages. The debug level 'n' and all
    below it are enabled by this option.
  * -d+n; Enables output of diagnostic messages. Only the output for debug
    level 'n' is enabled.

Debug Levels:

  Each debug level shows a different set of information. Usually with higher
  levels producing more verbose information. The following levels are supported:

  * 0; Turn off all diagnostic output. Only errors are reported.
  * 1; Show the actions taken for building targets, as they are executed.
  * 2; Show quiet actions and display all action text, as they are executed.
  * 3; Show dependency analysis, and target/source timestamps/paths.
  * 4; Show arguments of shell invocations.
  * 5; Show rule invocations and variable expansions.
  * 6; Show directory/header file/archive scans, and attempts at binding to
    targets.
  * 7; Show variable settings.
  * 8; Show variable fetches, variable expansions, and evaluation of 'if'
    expressions.
  * 9; Show variable manipulation, scanner tokens, and memory usage.
  * 10; Show execution times for rules.
  * 11; Show parsing progress of Jamfiles.
  * 12; Show graph for target dependencies.
  * 13; Show changes in target status (fate).

...found 1 target...
```

### Building sources

```
.\b2.exe toolset=msvc architecture=x86 address-model=32,64 threading=multi --prefix=D:\FILES\TOOLS\boost --build-dir=C:\Users\mg\Downloads\boost_1_71_0\build -sBZIP2_SOURCE="D:\FILES\TOOLS\bzip2-1.0.6" -sZLIB_SOURCE="D:\FILES\TOOLS\zlib-1.2.11" --build-type=complete --abbreviate-paths -j4 install
```

```
Performing configuration checks

    - default address-model    : 32-bit
    - default architecture     : x86
    - C++11 mutex              : yes
    - Boost.Config Feature Check: cxx11_auto_declarations : yes
    - Boost.Config Feature Check: cxx11_constexpr : yes
    - Boost.Config Feature Check: cxx11_defaulted_functions : yes
    - Boost.Config Feature Check: cxx11_final : yes
    - Boost.Config Feature Check: cxx11_hdr_mutex : yes
    - Boost.Config Feature Check: cxx11_hdr_tuple : yes
    - Boost.Config Feature Check: cxx11_lambdas : yes
    - Boost.Config Feature Check: cxx11_noexcept : yes
    - Boost.Config Feature Check: cxx11_nullptr : yes
    - Boost.Config Feature Check: cxx11_rvalue_references : yes
    - Boost.Config Feature Check: cxx11_template_aliases : yes
    - Boost.Config Feature Check: cxx11_thread_local : yes
    - Boost.Config Feature Check: cxx11_variadic_templates : yes
    - has_icu builds           : no
warning: Graph library does not contain MPI-based parallel components.
note: to enable them, add "using mpi ;" to your user-config.jam.
note: to suppress this message, pass "--without-graph_parallel" to bjam.
    - zlib                     : no
    - bzip2                    : no
    - lzma                     : no
    - zstd                     : no
    - iconv (libc)             : no
    - iconv (separate)         : no
    - icu                      : no
    - icu (lib64)              : no
    - native-atomic-int32-supported : yes
    - message-compiler         : yes
    - native-syslog-supported  : no
    - pthread-supports-robust-mutexes : no
    - compiler-supports-ssse3  : yes
    - compiler-supports-avx2   : yes
    - gcc visibility           : no
    - long double support      : yes
warning: skipping optional Message Passing Interface (MPI) library.
note: to enable MPI support, add "using mpi ;" to user-config.jam.
note: to suppress this message, pass "--without-mpi" to bjam.
note: otherwise, you can safely ignore this message.
warning: No python installation configured and autoconfiguration
note: failed.  See http://www.boost.org/libs/python/doc/building.html
note: for configuration instructions or pass --without-python to
note: suppress this message and silently skip all Boost.Python targets
    - libbacktrace builds      : no
    - addr2line builds         : no
    - WinDbg builds            : yes
    - WinDbgCached builds      : yes
    - BOOST_COMP_GNUC >= 4.3.0 : no
    - zlib                     : no  (cached)
    - bzip2                    : no  (cached)
    - lzma                     : no  (cached)
    - zstd                     : no  (cached)
    - zlib                     : no
    - bzip2                    : no
    - lzma                     : no
    - zstd                     : no
    - zlib                     : no  (cached)
    - bzip2                    : no  (cached)
    - lzma                     : no  (cached)
    - zstd                     : no  (cached)
    - zlib                     : no  (cached)
    - bzip2                    : no  (cached)
    - lzma                     : no  (cached)
    - zstd                     : no  (cached)
    - zlib                     : no  (cached)
    - bzip2                    : no  (cached)
    - lzma                     : no  (cached)
    - zstd                     : no  (cached)
    - C++11 mutex              : yes
    - Boost.Config Feature Check: cxx11_auto_declarations : yes
    - Boost.Config Feature Check: cxx11_constexpr : yes
    - Boost.Config Feature Check: cxx11_defaulted_functions : yes
    - Boost.Config Feature Check: cxx11_final : yes
    - Boost.Config Feature Check: cxx11_hdr_mutex : yes
    - Boost.Config Feature Check: cxx11_hdr_tuple : yes
    - Boost.Config Feature Check: cxx11_lambdas : yes
    - Boost.Config Feature Check: cxx11_noexcept : yes
    - Boost.Config Feature Check: cxx11_nullptr : yes
    - Boost.Config Feature Check: cxx11_rvalue_references : yes
    - Boost.Config Feature Check: cxx11_template_aliases : yes
    - Boost.Config Feature Check: cxx11_thread_local : yes
    - Boost.Config Feature Check: cxx11_variadic_templates : yes
    - has_icu builds           : no
    - zlib                     : no
    - bzip2                    : no
    - lzma                     : no
    - zstd                     : no
    - iconv (libc)             : no
    - iconv (separate)         : no
    - icu                      : no
    - icu (lib64)              : no
    - native-atomic-int32-supported : yes
    - message-compiler         : yes
    - native-syslog-supported  : no
    - pthread-supports-robust-mutexes : no
    - compiler-supports-ssse3  : yes
    - compiler-supports-avx2   : yes
    - gcc visibility           : no
    - long double support      : yes
    - libbacktrace builds      : no
    - addr2line builds         : no
    - WinDbg builds            : yes
    - WinDbgCached builds      : yes
    - BOOST_COMP_GNUC >= 4.3.0 : no
    - zlib                     : no  (cached)
    - bzip2                    : no  (cached)
    - lzma                     : no  (cached)
    - zstd                     : no  (cached)
    - zlib                     : no
    - bzip2                    : no
    - lzma                     : no
    - zstd                     : no  (cached)
    - zlib                     : no  (cached)
    - bzip2                    : no  (cached)
    - lzma                     : no  (cached)
    - zstd                     : no  (cached)
    - zlib                     : no  (cached)
    - bzip2                    : no  (cached)
    - lzma                     : no  (cached)
    - zstd                     : no  (cached)
...
```
