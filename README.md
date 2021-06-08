# conan-autoconf-ios-issue
Demo project for autoconf build error when cross-building from macOS to iOS

This project demonstrates what appears to be a bug in the autoconf Conan recipe when cross-building from MacOS for an iOS host. To reproduce, check out the project and run `conan install . --build missing -pr:h ios-profile` from the root directory. The resulting build failure is `autom4te: error: need GNU m4 1.4 or later: /usr/bin/env m4` despite a previous step building `m4 1.4.18` and setting an environment variable to its path.

<details open><summary>Full logs</summary>

```
➜ m4-bug-demo git:(main) conan install . --build missing -pr:h ios-profile
Configuration:
[settings]
arch=x86_64
build_type=Debug
compiler=apple-clang
compiler.cppstd=17
compiler.libcxx=libc++
compiler.version=12.0
os=iOS
os.version=12.0
[options]
[build_requires]
[env]

autoconf/2.71: Not found in local cache, looking in remotes...
autoconf/2.71: Trying with 'conan-center'...
Downloading conanmanifest.txt completed [1.05k]                                          
Downloading conanfile.py completed [4.79k]                                               
Downloading conan_export.tgz completed [0.39k]                                           
Decompressing conan_export.tgz completed [0.00k]                                         
autoconf/2.71: Downloaded recipe revision 0
m4/1.4.18: Not found in local cache, looking in remotes...
m4/1.4.18: Trying with 'conan-center'...
Downloading conanmanifest.txt completed [0.94k]                                          
Downloading conanfile.py completed [4.96k]                                               
Downloading conan_export.tgz completed [0.45k]                                           
Decompressing conan_export.tgz completed [0.00k]                                         
m4/1.4.18: Downloaded recipe revision 0
conanfile.txt: Installing package
Requirements
    autoconf/2.71 from 'conan-center' - Downloaded
    m4/1.4.18 from 'conan-center' - Downloaded
Packages
    autoconf/2.71:a728acd332aea736fea687b754a5e13cc4bdbb22 - Build
    m4/1.4.18:bbb2136fdf3bcb7760d73426671064455920f6c5 - Build

Cross-build from 'Macos:x86_64' to 'iOS:x86_64'
Installing (downloading, building) binaries...
Downloading conan_sources.tgz completed [6.39k]                                          
Decompressing conan_sources.tgz completed [0.00k]                                        
m4/1.4.18: Configuring sources in /Users/graeme/.conan/data/m4/1.4.18/_/_/source
Downloading m4-1.4.18.tar.bz2 completed [1481.41k]                                       

m4/1.4.18: Copying sources to build folder
m4/1.4.18: Building your package in /Users/graeme/.conan/data/m4/1.4.18/_/_/build/bbb2136fdf3bcb7760d73426671064455920f6c5
m4/1.4.18: Generator txt created conanbuildinfo.txt
m4/1.4.18: Calling build()
m4/1.4.18: Calling:
 > source_subfolder/configure '--prefix=/Users/graeme/.conan/data/m4/1.4.18/_/_/package/bbb2136fdf3bcb7760d73426671064455920f6c5' '--bindir=${prefix}/bin' '--sbindir=${prefix}/bin' '--libexecdir=${prefix}/bin' '--libdir=${prefix}/lib' '--includedir=${prefix}/include' '--oldincludedir=${prefix}/include' '--datarootdir=${prefix}/share' --build=x86_64-apple-darwin --host=x86_64-apple-ios
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for x86_64-apple-ios-strip... no
checking for strip... strip
configure: WARNING: using cross tools not prefixed with host triplet
checking for a thread-safe mkdir -p... source_subfolder/build-aux/install-sh -c -d
checking for gawk... no
checking for mawk... no
checking for nawk... no
checking for awk... awk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking whether make supports nested variables... (cached) yes
checking for x86_64-apple-ios-gcc... no
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables...
checking whether we are cross compiling... yes
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether gcc understands -c and -o together... rm: conftest.dSYM: is a directory
yes
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /usr/bin/grep
checking for egrep... /usr/bin/grep -E
checking for ANSI C header files... rm: conftest.dSYM: is a directory
rm: conftest.dSYM: is a directory
yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking whether _XOPEN_SOURCE should be defined... no
checking for Minix Amsterdam compiler... rm: conftest.dSYM: is a directory
no
checking for x86_64-apple-ios-ar... no
checking for x86_64-apple-ios-lib... no
checking for x86_64-apple-ios-link... no
checking for ar... ar
checking the archiver (ar) interface... ar
checking for x86_64-apple-ios-ar... ar
checking for x86_64-apple-ios-ranlib... no
checking for ranlib... ranlib
checking build system type... x86_64-apple-darwin
checking host system type... x86_64-apple-ios
checking for _LARGEFILE_SOURCE value needed for large files... no
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... no
checking for gcc option to accept ISO C99... none needed
checking for gcc option to accept ISO Standard C... (cached) none needed
configure: autobuild project... GNU M4
configure: autobuild revision... 1.4.18
configure: autobuild hostname... redacted.host.name
configure: autobuild timestamp... 20210608T122323Z
checking for unsigned long long int... yes
checking for long long int... yes
checking for unsigned long long int... (cached) yes
checking for size_t... yes
checking for working alloca.h... yes
checking for alloca... yes
checking whether <wchar.h> uses 'inline' correctly... yes
checking for btowc... yes
checking for setrlimit... yes
checking for sigaltstack... yes
checking for canonicalize_file_name... no
checking for getcwd... yes
checking for readlink... yes
checking for realpath... yes
checking for _set_invalid_parameter_handler... no
checking for fcntl... yes
checking for symlink... yes
checking for mempcpy... no
checking for fpurge... yes
checking for __fpurge... no
checking for __freadahead... no
checking for __freading... no
checking for getdtablesize... yes
checking for getprogname... yes
checking for getexecname... no
checking for gettimeofday... yes
checking for lstat... yes
checking for mbsinit... yes
checking for mbrtowc... yes
checking for mprotect... yes
checking for mkstemp... yes
checking for nl_langinfo... yes
checking for pipe2... no
checking for isblank... yes
checking for iswctype... yes
checking for link... yes
checking for secure_getenv... no
checking for getuid... yes
checking for geteuid... yes
checking for getgid... yes
checking for getegid... yes
checking for sigaction... yes
checking for siginterrupt... yes
checking for snprintf... yes
checking for strndup... yes
checking for pipe... yes
checking for vasnprintf... no
checking for wcrtomb... yes
checking for iswcntrl... yes
checking for newlocale... yes
checking for setenv... yes
checking for sleep... yes
checking for strdup... yes
checking for wctob... yes
checking for nl_langinfo and CODESET... yes
checking for a traditional french locale... none
checking for ucontext.h... no
checking for unistd.h... (cached) yes
checking for sys/param.h... yes
checking for sys/socket.h... yes
checking for stdio_ext.h... no
checking for sys/stat.h... (cached) yes
checking for getopt.h... yes
checking for sys/time.h... yes
checking for langinfo.h... yes
checking for limits.h... yes
checking for xlocale.h... yes
checking for math.h... yes
checking for sys/mman.h... yes
checking for malloc.h... no
checking for sys/cdefs.h... yes
checking for spawn.h... yes
checking for wchar.h... yes
checking for stdint.h... (cached) yes
checking for sys/wait.h... yes
checking for features.h... no
checking for wctype.h... yes
checking for dirent.h... yes
checking for inttypes.h... (cached) yes
checking for working C stack overflow detection... cross-compiling
checking for ld used by gcc... /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ld
checking if the linker (/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ld) is GNU ld... no
checking for shared library run path origin... done
checking for libsigsegv... no, consider installing GNU libsigsegv
checking whether // is distinct from /... unknown, assuming no
checking whether realpath works... guessing no
checking if environ is properly declared... no
checking whether the preprocessor supports include_next... yes
checking whether system header files limit the line length... no
checking for complete errno.h... yes
checking whether strerror_r is declared... yes
checking for strerror_r... yes
checking whether strerror_r returns char *... no
checking for mode_t... yes
checking for sig_atomic_t... yes
checking for working fcntl.h... cross-compiling
checking for pid_t... yes
checking whether frexp() can be used without linking with libm... yes
checking whether alarm is declared... yes
checking whether long double and double are the same... no
checking whether stdin defaults to large file offsets... yes
checking whether fseeko is declared... yes
checking for fseeko... yes
checking whether fflush works on input streams... cross
checking whether stat file-mode macros are broken... no
checking for nlink_t... yes
checking whether ftello is declared... yes
checking for ftello... yes
checking whether ftello works... guessing yes
checking whether getdtablesize is declared... yes
checking for getopt.h... (cached) yes
checking for getopt_long_only... yes
checking whether getopt is POSIX compatible... guessing yes
checking for working GNU getopt function... guessing no
checking whether getenv is declared... yes
checking for C/C++ restrict keyword... __restrict
checking for struct timeval... yes
checking for wide-enough struct timeval.tv_sec member... yes
checking where to find the exponent in a 'double'... word 1 bit 20
checking where to find the exponent in a 'float'... word 0 bit 23
checking whether byte ordering is bigendian... (cached) no
checking whether limits.h has ULLONG_WIDTH etc.... no
checking whether getc_unlocked is declared... yes
checking whether we are using the GNU C Library >= 2.1 or uClibc... no
checking for wchar_t... yes
checking for max_align_t... yes
checking whether NULL can be used in arbitrary expressions... yes
checking for multithread API to use... none
checking whether lstat correctly handles trailing slash... guessing no
checking for a sed that does not truncate output... /usr/bin/sed
checking whether malloc, realloc, calloc are POSIX compliant... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... no
checking for mbstate_t... yes
checking for a traditional japanese locale... ja_JP.eucJP
checking for a transitional chinese locale... none
checking for a french Unicode locale... none
checking for mmap... yes
checking for MAP_ANONYMOUS... yes
checking whether memchr works... guessing no
checking whether <limits.h> defines MIN and MAX... no
checking whether <sys/param.h> defines MIN and MAX... yes
checking for promoted mode_t type... int
checking for library containing posix_spawn... none required
checking for posix_spawn... yes
checking whether posix_spawn works... guessing yes
checking whether posix_spawnattr_setschedpolicy is supported... no
checking whether posix_spawnattr_setschedparam is supported... no
checking for sigset_t... yes
checking for SIGPIPE... yes
checking for inline... inline
checking for uid_t in sys/types.h... yes
checking whether C symbols are prefixed with underscore at the linker level... yes
checking whether snprintf returns a byte count as in C99... guessing no
checking whether snprintf is declared... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for wint_t... yes
checking whether wint_t is too small... no
checking whether stdint.h conforms to C99... yes
checking whether stdint.h predates C++11... no
checking whether stdint.h has UINTMAX_WIDTH etc.... no
checking whether strerror(0) succeeds... guessing no
checking whether strndup is declared... yes
checking whether strnlen is declared... yes
checking whether strsignal is declared... yes
checking whether sys_siglist is declared... yes
checking whether ldexp() can be used without linking with libm... yes
checking for struct timespec in <time.h>... yes
checking whether clearerr_unlocked is declared... yes
checking whether feof_unlocked is declared... yes
checking whether ferror_unlocked is declared... yes
checking whether fflush_unlocked is declared... no
checking whether fgets_unlocked is declared... no
checking whether fputc_unlocked is declared... no
checking whether fputs_unlocked is declared... no
checking whether fread_unlocked is declared... no
checking whether fwrite_unlocked is declared... no
checking whether getchar_unlocked is declared... yes
checking whether putc_unlocked is declared... yes
checking whether putchar_unlocked is declared... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for intmax_t... yes
checking for snprintf... (cached) yes
checking for strnlen... yes
checking for wcslen... yes
checking for wcsnlen... yes
checking for mbrtowc... (cached) yes
checking for wcrtomb... (cached) yes
checking whether _snprintf is declared... no
checking whether printf supports size specifiers as in C99... guessing no
checking whether printf supports 'long double' arguments... guessing yes
checking whether printf supports infinite 'double' arguments... guessing no
checking whether printf supports infinite 'long double' arguments... guessing no
checking whether printf supports the 'a' and 'A' directives... guessing no
checking whether printf supports the 'F' directive... guessing no
checking whether printf supports the 'n' directive... guessing yes
checking whether printf supports the 'ls' directive... guessing yes
checking whether printf supports the grouping flag... guessing yes
checking whether printf supports the left-adjust flag correctly... guessing yes
checking whether printf supports the zero flag correctly... guessing no
checking whether printf supports large precisions... guessing yes
checking whether printf survives out-of-memory conditions... guessing no
checking whether to use C++... no
checking whether ungetc works on arbitrary bytes... guessing no
checking whether getcwd (NULL, 0) allocates memory for result... guessing no
checking for getcwd with POSIX signature... yes
checking for inttypes.h... (cached) yes
checking whether the inttypes.h PRIxNN macros are broken... no
checking for LC_MESSAGES... yes
checking for CFPreferencesCopyAppValue... yes
checking for CFLocaleCopyCurrent... yes
checking whether setenv is declared... yes
checking search.h usability... yes
checking search.h presence... yes
checking for search.h... yes
checking for tsearch... yes
checking whether strdup is declared... yes
checking whether unsetenv is declared... yes
checking for alloca as a compiler built-in... yes
checking whether to enable assertions... yes
checking whether btowc(0) is correct... guessing yes
checking whether btowc(EOF) is correct... guessing yes
checking for __builtin_expect... yes
checking whether sigaltstack is declared... yes
checking for stack_t... yes
checking whether // is distinct from /... (cached) unknown, assuming no
checking whether dup2 works... guessing yes
checking for error_at_line... no
checking whether fflush works on input streams... (cached) cross
checking whether fcntl handles F_DUPFD correctly... guessing yes
checking whether fcntl understands F_DUPFD_CLOEXEC... yes
checking whether fflush works on input streams... (cached) cross
checking whether conversion from 'int' to 'long double' works... guessing yes
checking whether fopen recognizes a trailing slash... guessing yes
checking for __fpending... no
checking whether fpurge is declared... yes
checking whether fpurge works... guessing no
checking whether frexp works... guessing yes
checking whether frexpl is declared... yes
checking whether frexpl() can be used without linking with libm... yes
checking whether frexpl works... guessing yes
checking for fseeko... (cached) yes
checking whether fflush works on input streams... (cached) cross
checking for _fseeki64... no
checking for ftello... (cached) yes
checking whether ftello works... (cached) guessing yes
checking whether getdtablesize works... guessing yes
checking whether program_invocation_name is declared... no
checking whether program_invocation_short_name is declared... no
checking whether __argv is declared... no
checking whether __progname is defined in default libraries... yes
checking whether gettimeofday clobbers localtime buffer... guessing yes
checking for gettimeofday with POSIX signature... yes
checking sys/timeb.h usability... yes
checking sys/timeb.h presence... yes
checking for sys/timeb.h... yes
checking for _ftime... no
checking whether isnan(double) can be used without linking with libm... yes
checking whether isnan(float) can be used without linking with libm... no
checking where to find the exponent in a 'float'... (cached) word 0 bit 23
checking whether isnan(long double) can be used without linking with libm... no
checking where to find the exponent in a 'long double'... unknown
checking whether langinfo.h defines CODESET... yes
checking whether langinfo.h defines T_FMT_AMPM... yes
checking whether langinfo.h defines ERA... yes
checking whether langinfo.h defines YESEXPR... yes
checking for libsigsegv... (cached) no, consider installing GNU libsigsegv
checking whether locale.h conforms to POSIX:2001... yes
checking whether locale.h defines locale_t... no
checking whether struct lconv is properly defined... yes
checking whether lseek detects pipes... yes
checking whether NAN macro works... yes
checking whether HUGE_VAL works... yes
checking whether mbrtowc handles incomplete characters... guessing yes
checking whether mbrtowc works as well as mbtowc... guessing yes
checking whether mbrtowc handles a NULL pwc argument... guessing yes
checking whether mbrtowc handles a NULL string argument... guessing yes
checking whether mbrtowc has a correct return value... guessing yes
checking whether mbrtowc returns 0 when parsing a NUL character... guessing yes
checking whether mbrtowc works on empty input... guessing yes
checking whether the C locale is free of encoding errors... guessing no
checking whether mbrtowc handles incomplete characters... (cached) guessing yes
checking whether mbrtowc works as well as mbtowc... (cached) guessing yes
checking bp-sym.h usability... no
checking bp-sym.h presence... no
checking for bp-sym.h... no
checking for mkdtemp... yes
checking for working mkstemp... guessing no
checking whether YESEXPR works... guessing yes
checking for obstacks that work with any size object... no
checking whether open recognizes a trailing slash... guessing yes
checking whether posix_spawn_file_actions_addclose works... guessing yes
checking whether posix_spawn_file_actions_adddup2 works... guessing yes
checking whether posix_spawn_file_actions_addopen works... guessing yes
checking whether frexp works... (cached) guessing yes
checking whether ldexp can be used without linking with libm... (cached) yes
checking whether frexpl() can be used without linking with libm... (cached) yes
checking whether frexpl works... (cached) guessing yes
checking whether frexpl is declared... (cached) yes
checking whether ldexpl() can be used without linking with libm... yes
checking whether ldexpl works... guessing yes
checking whether ldexpl is declared... yes
checking whether program_invocation_name is declared... (cached) no
checking whether program_invocation_short_name is declared... (cached) no
checking for raise... yes
checking for sigprocmask... yes
checking for rawmemchr... no
checking whether readlink signature is correct... yes
checking whether readlink handles trailing slash correctly... guessing no
checking for working re_compile_pattern... no
checking libintl.h usability... no
checking libintl.h presence... yes
configure: WARNING: libintl.h: present but cannot be compiled
configure: WARNING: libintl.h:     check for missing prerequisite headers?
configure: WARNING: libintl.h: see the Autoconf documentation
configure: WARNING: libintl.h:     section "Present But Cannot Be Compiled"
configure: WARNING: libintl.h: proceeding with the compiler's result
configure: WARNING:     ## ----------------------------- ##
configure: WARNING:     ## Report this to bug-m4@gnu.org ##
configure: WARNING:     ## ----------------------------- ##
checking for libintl.h... no
checking whether isblank is declared... yes
checking whether rename honors trailing slash on destination... guessing no
checking whether rename honors trailing slash on source... guessing no
checking whether rename manages hard links correctly... guessing no
checking whether rename manages existing destinations correctly... guessing no
checking whether rmdir works... guessing no
checking for sched.h... yes
checking for struct sched_param... yes
checking for __secure_getenv... no
checking for issetugid... yes
checking for struct sigaction.sa_sigaction... yes
checking for volatile sig_atomic_t... yes
checking for sighandler_t... no
checking for signbit macro... guessing no
checking for signbit compiler built-ins... guessing no
checking where to find the sign bit in a 'float'... unknown
checking where to find the sign bit in a 'double'... unknown
checking where to find the sign bit in a 'long double'... unknown
checking whether copysignf is declared... yes
checking whether copysignf can be used without linking with libm... yes
checking whether copysign is declared... yes
checking whether copysign can be used without linking with libm... yes
checking whether copysignl is declared... yes
checking whether copysignl can be used without linking with libm... yes
checking for sigprocmask... (cached) yes
checking for stdint.h... (cached) yes
checking for SIZE_MAX... yes
checking for snprintf... (cached) yes
checking whether snprintf respects a size of 1... guessing yes
checking for posix_spawnattr_t... yes
checking for posix_spawn_file_actions_t... yes
checking for ssize_t... yes
checking whether stat handles trailing slashes on directories... guessing yes
checking whether stat handles trailing slashes on files... guessing no
checking for va_copy... yes
checking for max_align_t... (cached) yes
checking whether NULL can be used in arbitrary expressions... (cached) yes
checking which flavor of printf attribute matches inttypes macros... system
checking for strchrnul... no
checking for working strndup... guessing yes
checking for working strnlen... yes
checking for strsignal... yes
checking whether strsignal always returns a string... guessing yes
checking whether strtod obeys C99... guessing no
checking for nlink_t... (cached) yes
checking for ptrdiff_t... yes
checking for vasprintf... yes
checking for vasprintf... (cached) yes
checking for nl_langinfo... (cached) yes
checking for ptrdiff_t... (cached) yes
checking for waitid... yes
checking whether mbrtowc handles incomplete characters... (cached) guessing yes
checking whether mbrtowc works as well as mbtowc... (cached) guessing yes
checking whether wcrtomb return value is correct... guessing yes
checking whether iswcntrl works... guessing yes
checking for towlower... yes
checking for wctype_t... yes
checking for wctrans_t... yes
checking for stdint.h... (cached) yes
checking for a traditional french locale... (cached) none
checking for a french Unicode locale... (cached) none
checking for a traditional french locale... (cached) none
checking for a turkish Unicode locale... none
checking for closedir... yes
checking for dirfd... yes
checking whether dirfd is declared... yes
checking whether dirfd is a macro... no
checking whether dup works... guessing yes
checking whether fdopen sets errno... guessing yes
checking for flexible array member... yes
checking for getpagesize... yes
checking whether getpagesize is declared... yes
checking whether INT32_MAX < INTMAX_MAX... yes
checking whether INT64_MAX == LONG_MAX... yes
checking whether UINT32_MAX < UINTMAX_MAX... yes
checking whether UINT64_MAX == ULONG_MAX... yes
checking where to find the exponent in a 'double'... (cached) word 1 bit 20
checking where to find the exponent in a 'float'... (cached) word 0 bit 23
checking where to find the exponent in a 'long double'... (cached) unknown
checking whether link obeys POSIX... guessing no
checking for setlocale... yes
checking for uselocale... yes
checking for getlocalename_l... no
checking for a traditional french locale... (cached) none
checking for a french Unicode locale... (cached) none
checking for a traditional japanese locale... (cached) ja_JP.eucJP
checking for a transitional chinese locale... (cached) none
checking for a french Unicode locale... (cached) none
checking for mmap... (cached) yes
checking for MAP_ANONYMOUS... yes
checking for mmap... (cached) yes
checking for MAP_ANONYMOUS... yes
checking for a traditional french locale... (cached) none
checking for a french Unicode locale... (cached) none
checking for opendir... yes
checking for putenv compatible with GNU and SVID... guessing no
checking whether _putenv is declared... no
checking for mmap... (cached) yes
checking for MAP_ANONYMOUS... yes
checking for mmap... (cached) yes
checking for MAP_ANONYMOUS... yes
checking for readdir... yes
checking whether setenv validates arguments... guessing no
checking for a traditional french locale... (cached) none
checking for a french Unicode locale... (cached) none
checking for a traditional japanese locale... (cached) ja_JP.eucJP
checking for a transitional chinese locale... (cached) none
checking whether sleep is declared... yes
checking for working sleep... guessing no
checking for working stdalign.h... yes
checking for mmap... (cached) yes
checking for MAP_ANONYMOUS... yes
checking for mmap... (cached) yes
checking for MAP_ANONYMOUS... yes
checking whether symlink handles trailing slash correctly... guessing no
checking for unsetenv... yes
checking for unsetenv() return type... int
checking whether unsetenv obeys POSIX... guessing no
checking for a traditional french locale... (cached) none
checking for a french Unicode locale... (cached) none
checking for a traditional japanese locale... (cached) ja_JP.eucJP
checking for a transitional chinese locale... (cached) none
checking whether wctob works... guessing yes
checking whether wctob is declared... yes
checking whether an open file can be renamed... guessing no
checking if changeword is wanted... no
checking which shell to use for syscmd... /bin/sh
checking if malloc debugging is wanted... no
checking that generated files are newer than configure... done
configure: creating ./config.status
config.status: creating Makefile
config.status: creating doc/Makefile
config.status: creating lib/Makefile
config.status: creating src/Makefile
config.status: creating tests/Makefile
config.status: creating checks/Makefile
config.status: creating examples/Makefile
config.status: creating lib/config.h
config.status: linking source_subfolder/GNUmakefile to GNUmakefile
config.status: executing depfiles commands
config.status: executing stamp-h commands
/Applications/Xcode.app/Contents/Developer/usr/bin/make  all-recursive
Making all in .
make[2]: Nothing to be done for `all-am'.
Making all in examples
make[2]: Nothing to be done for `all'.
Making all in lib
  GEN      alloca.h
  GEN      configmake.h
  GEN      c++defs.h
  GEN      arg-nonnull.h
  GEN      warn-on-use.h
  GEN      limits.h
  GEN      sched.h
  GEN      unused-parameter.h
  GEN      stdint.h
  GEN      getopt.h
  GEN      fcntl.h
  GEN      langinfo.h
  GEN      locale.h
  GEN      math.h
  GEN      signal.h
  GEN      spawn.h
  GEN      stdio.h
  GEN      stdlib.h
  GEN      string.h
  GEN      time.h
  GEN      unistd.h
  GEN      wchar.h
  GEN      wctype.h
mkdir: mkdir: syssys: : File exists
File exists
mkdir: sys: File exists
  GEN      sys/wait.h
  GEN      sys/time.h
  GEN      sys/stat.h
  GEN      sys/types.h
/Applications/Xcode.app/Contents/Developer/usr/bin/make  all-am
  CC       gl_avltree_oset.o
  CC       binary-io.o
  CC       c-ctype.o
  CC       c-stack.o
  CC       c-strncasecmp.o
  CC       c-strcasecmp.o
  CC       clean-temp.o
  CC       cloexec.o
  CC       close-stream.o
  CC       closein.o
  CC       closeout.o
  CC       dirname.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: clang: warning: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clangclang: : warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]warning:
argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       basename.o
  CC       dirname-lgpl.o
  CC       basename-lgpl.o
  CC       stripslash.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       execute.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       exitfail.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       fatal-signal.o
  CC       fd-hook.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       fd-safer-flag.o
  CC       dup-safer-flag.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       filenamecat.o
  CC       filenamecat-lgpl.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       fopen-safer.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       freading.o
  CC       getprogname.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       hard-locale.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       gl_linkedhash_list.o
  CC       gl_list.o
  CC       localcharset.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       malloca.o
  CC       math.o
  CC       memchr2.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       gl_oset.o
  CC       pipe2.o
  CC       pipe2-safer.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       printf-frexp.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       printf-frexpl.o
  CC       progname.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       quotearg.o
  CC       sig-handler.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       spawn-pipe.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       mkstemp-safer.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       tempname.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       glthread/threadlib.o
  CC       glthread/tls.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       tmpdir.o
  CC       unistd.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       dup-safer.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       fd-safer.o
  CC       pipe-safer.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       verror.o
  CC       version-etc.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       version-etc-fsf.o
  CC       wait-process.o
  CC       wctype-h.o
  CC       xmalloc.o
  CC       xalloc-die.o
  CC       gl_xlist.o
  CC       xmalloca.o
  CC       gl_xoset.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       xprintf.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       xsize.o
  CC       xstrndup.o
  CC       xvasprintf.o
  CC       xasprintf.o
  CC       asnprintf.o
  CC       asprintf.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       canonicalize-lgpl.o
  CC       error.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       fclose.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       fflush.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       fpending.o
  CC       fpurge.o
  CC       freadahead.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       fseek.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       fseeko.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       getopt.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       getopt1.o
  CC       gettimeofday.o
  CC       isnanf.o
  CC       isnanl.o
  CC       lstat.o
  CC       mbrtowc.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       memchr.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       mkstemp.o
  CC       obstack.o
  CC       printf-args.o
  CC       printf-parse.o
  CC       rawmemchr.o
  CC       readlink.o
  CC       regex.o
  CC       rename.o
  CC       rmdir.o
  CC       secure_getenv.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       signbitd.o
../source_subfolder/lib/obstack.c:351:31: warning: incompatible pointer types initializing 'void (*)(void) __attribute__((noreturn))' with an expression of type 'void (void)'
      [-Wincompatible-pointer-types]
__attribute_noreturn__ void (*obstack_alloc_failed_handler) (void)
                              ^
1 warning generated.
  CC       signbitf.o
  CC       signbitl.o
  CC       snprintf.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       stat.o
  CC       strchrnul.o
  CC       strerror.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       strerror-override.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       strstr.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CC       strtod.o
  CC       vasnprintf.o
  CC       vasprintf.o
  GEN      charset.alias
  GEN      ref-add.sed
  GEN      ref-del.sed
  CC       glthread/lock.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  AR       libm4.a
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: libm4.a(binary-io.o) has no symbols
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: libm4.a(c-ctype.o) has no symbols
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: libm4.a(fd-hook.o) has no symbols
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: libm4.a(getprogname.o) has no symbols
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: libm4.a(gl_list.o) has no symbols
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: libm4.a(lock.o) has no symbols
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: libm4.a(math.o) has no symbols
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: libm4.a(gl_oset.o) has no symbols
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: libm4.a(sig-handler.o) has no symbols
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: libm4.a(threadlib.o) has no symbols
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: libm4.a(tls.o) has no symbols
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: libm4.a(unistd.o) has no symbols
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: libm4.a(wctype-h.o) has no symbols
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: libm4.a(gl_xlist.o) has no symbols
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: libm4.a(gl_xoset.o) has no symbols
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: libm4.a(xsize.o) has no symbols
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: libm4.a(binary-io.o) has no symbols
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: libm4.a(c-ctype.o) has no symbols
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: libm4.a(fd-hook.o) has no symbols
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: libm4.a(getprogname.o) has no symbols
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: libm4.a(gl_list.o) has no symbols
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: libm4.a(lock.o) has no symbols
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: libm4.a(math.o) has no symbols
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: libm4.a(gl_oset.o) has no symbols
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: libm4.a(sig-handler.o) has no symbols
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: libm4.a(threadlib.o) has no symbols
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: libm4.a(tls.o) has no symbols
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: libm4.a(unistd.o) has no symbols
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: libm4.a(wctype-h.o) has no symbols
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: libm4.a(gl_xlist.o) has no symbols
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: libm4.a(gl_xoset.o) has no symbols
/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ranlib: file: libm4.a(xsize.o) has no symbols
Making all in src
  CC       m4.o
  CC       builtin.o
  CC       debug.o
  CC       eval.o
  CC       format.o
  CC       freeze.o
  CC       macro.o
  CC       input.o
  CC       output.o
  CC       path.o
  CC       symtab.o
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: clangwarning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
clang: warning: argument unused during compilation: '-rtlib=compiler-rt' [-Wunused-command-line-argument]
  CCLD     m4
Making all in doc
make[2]: Nothing to be done for `all'.
Making all in checks
make[2]: Nothing to be done for `all'.
Making all in tests
  GEN      c++defs.h
  GEN      warn-on-use.h
  GEN      arg-nonnull.h
  GEN      test-posix_spawn1.sh
  GEN      test-posix_spawn2.sh
  GEN      unused-parameter.h
  GEN      ctype.h
  GEN      dirent.h
  GEN      inttypes.h
/Applications/Xcode.app/Contents/Developer/usr/bin/make  all-recursive
Making all in .
make[4]: Nothing to be done for `all-am'.
m4/1.4.18: Package 'bbb2136fdf3bcb7760d73426671064455920f6c5' built
m4/1.4.18: Build folder /Users/graeme/.conan/data/m4/1.4.18/_/_/build/bbb2136fdf3bcb7760d73426671064455920f6c5
m4/1.4.18: Generated conaninfo.txt
m4/1.4.18: Generated conanbuildinfo.txt
m4/1.4.18: Generating the package
m4/1.4.18: Package folder /Users/graeme/.conan/data/m4/1.4.18/_/_/package/bbb2136fdf3bcb7760d73426671064455920f6c5
m4/1.4.18: Calling package()
/Applications/Xcode.app/Contents/Developer/usr/bin/make  install-recursive
Making install in .
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
Making install in examples
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
Making install in lib
/Applications/Xcode.app/Contents/Developer/usr/bin/make  install-am
if test no = no; then \
	  case 'ios' in \
	    darwin[56]*) \
	      need_charset_alias=true ;; \
	    darwin* | cygwin* | mingw* | pw32* | cegcc*) \
	      need_charset_alias=false ;; \
	    *) \
	      need_charset_alias=true ;; \
	  esac ; \
	else \
	  need_charset_alias=false ; \
	fi ; \
	if $need_charset_alias; then \
	  /bin/sh /Users/graeme/.conan/data/m4/1.4.18/_/_/build/bbb2136fdf3bcb7760d73426671064455920f6c5/source_subfolder/build-aux/install-sh -d /Users/graeme/.conan/data/m4/1.4.18/_/_/package/bbb2136fdf3bcb7760d73426671064455920f6c5/lib ; \
	fi ; \
	if test -f /Users/graeme/.conan/data/m4/1.4.18/_/_/package/bbb2136fdf3bcb7760d73426671064455920f6c5/lib/charset.alias; then \
	  sed -f ref-add.sed /Users/graeme/.conan/data/m4/1.4.18/_/_/package/bbb2136fdf3bcb7760d73426671064455920f6c5/lib/charset.alias > /Users/graeme/.conan/data/m4/1.4.18/_/_/package/bbb2136fdf3bcb7760d73426671064455920f6c5/lib/charset.tmp ; \
	  /usr/bin/install -c -m 644 /Users/graeme/.conan/data/m4/1.4.18/_/_/package/bbb2136fdf3bcb7760d73426671064455920f6c5/lib/charset.tmp /Users/graeme/.conan/data/m4/1.4.18/_/_/package/bbb2136fdf3bcb7760d73426671064455920f6c5/lib/charset.alias ; \
	  rm -f /Users/graeme/.conan/data/m4/1.4.18/_/_/package/bbb2136fdf3bcb7760d73426671064455920f6c5/lib/charset.tmp ; \
	else \
	  if $need_charset_alias; then \
	    sed -f ref-add.sed charset.alias > /Users/graeme/.conan/data/m4/1.4.18/_/_/package/bbb2136fdf3bcb7760d73426671064455920f6c5/lib/charset.tmp ; \
	    /usr/bin/install -c -m 644 /Users/graeme/.conan/data/m4/1.4.18/_/_/package/bbb2136fdf3bcb7760d73426671064455920f6c5/lib/charset.tmp /Users/graeme/.conan/data/m4/1.4.18/_/_/package/bbb2136fdf3bcb7760d73426671064455920f6c5/lib/charset.alias ; \
	    rm -f /Users/graeme/.conan/data/m4/1.4.18/_/_/package/bbb2136fdf3bcb7760d73426671064455920f6c5/lib/charset.tmp ; \
	  fi ; \
	fi
make[4]: Nothing to be done for `install-data-am'.
Making install in src
make[3]: Nothing to be done for `install-data-am'.
 ../source_subfolder/build-aux/install-sh -c -d '/Users/graeme/.conan/data/m4/1.4.18/_/_/package/bbb2136fdf3bcb7760d73426671064455920f6c5/bin'
  /usr/bin/install -c m4 '/Users/graeme/.conan/data/m4/1.4.18/_/_/package/bbb2136fdf3bcb7760d73426671064455920f6c5/bin'
Making install in doc
make[3]: Nothing to be done for `install-exec-am'.
 ../source_subfolder/build-aux/install-sh -c -d '/Users/graeme/.conan/data/m4/1.4.18/_/_/package/bbb2136fdf3bcb7760d73426671064455920f6c5/share/man/man1'
 ../source_subfolder/build-aux/install-sh -c -d '/Users/graeme/.conan/data/m4/1.4.18/_/_/package/bbb2136fdf3bcb7760d73426671064455920f6c5/share/info'
mkdir: /Users/graeme/.conan/data/m4/1.4.18/_/_/package/bbb2136fdf3bcb7760d73426671064455920f6c5/share: File exists
 /usr/bin/install -c -m 644 ../source_subfolder/doc/m4.1 '/Users/graeme/.conan/data/m4/1.4.18/_/_/package/bbb2136fdf3bcb7760d73426671064455920f6c5/share/man/man1'
 /usr/bin/install -c -m 644 ../source_subfolder/doc/m4.info ../source_subfolder/doc/m4.info-1 ../source_subfolder/doc/m4.info-2 '/Users/graeme/.conan/data/m4/1.4.18/_/_/package/bbb2136fdf3bcb7760d73426671064455920f6c5/share/info'
 install-info --info-dir='/Users/graeme/.conan/data/m4/1.4.18/_/_/package/bbb2136fdf3bcb7760d73426671064455920f6c5/share/info' '/Users/graeme/.conan/data/m4/1.4.18/_/_/package/bbb2136fdf3bcb7760d73426671064455920f6c5/share/info/m4.info'
Making install in checks
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
Making install in tests
/Applications/Xcode.app/Contents/Developer/usr/bin/make  install-recursive
Making install in .
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
m4/1.4.18 package(): Packaged 2 files: m4, COPYING
m4/1.4.18 package(): Packaged 1 '.alias' file: charset.alias
m4/1.4.18: Package 'bbb2136fdf3bcb7760d73426671064455920f6c5' created
m4/1.4.18: Created package revision c6905aa54488b0c9ee5f744ee00cdafa
m4/1.4.18: Appending PATH environment variable: /Users/graeme/.conan/data/m4/1.4.18/_/_/package/bbb2136fdf3bcb7760d73426671064455920f6c5/bin
m4/1.4.18: Setting M4 environment variable: /Users/graeme/.conan/data/m4/1.4.18/_/_/package/bbb2136fdf3bcb7760d73426671064455920f6c5/bin/m4
Downloading conan_sources.tgz completed [2.88k]                                          
Decompressing conan_sources.tgz completed [0.00k]                                        
autoconf/2.71: Configuring sources in /Users/graeme/.conan/data/autoconf/2.71/_/_/source
Downloading autoconf-2.71.tar.gz completed [1956.82k]                                    

autoconf/2.71: Copying sources to build folder
autoconf/2.71: Building your package in /Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22
autoconf/2.71: Generator txt created conanbuildinfo.txt
autoconf/2.71: Calling build()
autoconf/2.71: Calling:
 > /Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/configure '--datarootdir=/Users/graeme/.conan/data/autoconf/2.71/_/_/package/a728acd332aea736fea687b754a5e13cc4bdbb22/bin/share' '--prefix=/Users/graeme/.conan/data/autoconf/2.71/_/_/package/a728acd332aea736fea687b754a5e13cc4bdbb22' '--bindir=${prefix}/bin' '--sbindir=${prefix}/bin' '--libexecdir=${prefix}/bin' '--libdir=${prefix}/lib' '--includedir=${prefix}/include' '--oldincludedir=${prefix}/include' --build=x86_64-apple-darwin --host=x86_64-apple-ios
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for x86_64-apple-ios-strip... no
checking for strip... strip
configure: WARNING: using cross tools not prefixed with host triplet
checking for a race-free mkdir -p... /Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/build-aux/install-sh -c -d
checking for gawk... no
checking for mawk... no
checking for nawk... no
checking for awk... awk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking build system type... x86_64-apple-darwin
checking host system type... x86_64-apple-ios
configure: autobuild project... GNU Autoconf
configure: autobuild revision... 2.71
configure: autobuild hostname... Graemes-MBP-2.fritz.box
configure: autobuild timestamp... 20210608T122408Z
checking for a shell whose -n mode is known to work... /bin/sh
checking for characters that cannot appear in file names... none
checking whether directories can have trailing spaces... yes
checking for expr... /bin/expr
checking for GNU M4 that supports accurate traces... /Users/graeme/.conan/data/m4/1.4.18/_/_/package/bbb2136fdf3bcb7760d73426671064455920f6c5/bin/m4
checking whether /Users/graeme/.conan/data/m4/1.4.18/_/_/package/bbb2136fdf3bcb7760d73426671064455920f6c5/bin/m4 accepts --gnu... no
configure: WARNING: the version of M4 that was found does not support -g
configure: WARNING: using it with POSIXLY_CORRECT set may cause problems
checking how m4 supports trace files... --error-output
checking for perl... /usr/bin/perl
checking whether /usr/bin/perl Fcntl::flock is implemented... yes
checking for emacs... emacs
checking whether emacs is sufficiently recent... yes
checking for emacs... emacs
checking where .elc files should go... ${datadir}/emacs/site-lisp
checking for grep that handles long lines and -e... /usr/bin/grep
checking for egrep... /usr/bin/grep -E
checking for a sed that does not truncate output... /usr/bin/sed
checking whether make is case sensitive... yes
checking that generated files are newer than configure... done
configure: creating ./config.status
config.status: creating tests/atlocal
config.status: creating Makefile
config.status: linking /Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/GNUmakefile to GNUmakefile
config.status: executing tests/atconfig commands
/Applications/Xcode.app/Contents/Developer/usr/bin/make  all-am
rm -f bin/autom4te bin/autom4te.tmp
rm -f lib/autom4te.cfg lib/autom4te.cfg-t
/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/build-aux/install-sh -c -d bin
/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/build-aux/install-sh -c -d lib/m4sugar
/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/build-aux/install-sh -c -d lib
rm -f bin/autoheader bin/autoheader.tmp
rm -f bin/autoreconf bin/autoreconf.tmp
/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/build-aux/install-sh -c -d bin
rm -f bin/autoscan bin/autoscan.tmp
/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/build-aux/install-sh -c -d bin
rm -f bin/autoupdate bin/autoupdate.tmp
/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/build-aux/install-sh -c -d bin
rm -f bin/ifnames bin/ifnames.tmp
/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/build-aux/install-sh -c -d bin
if test 'emacs' != no; then \
	  am__dir=. am__subdir_includes=''; \
	  case lib/emacs/autoconf-mode.elc in */*) \
	    am__dir=`echo 'lib/emacs/autoconf-mode.elc' | sed 's,/[^/]*$,,'`; \
	    am__subdir_includes="-L $am__dir -L /Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/$am__dir"; \
	  esac; \
	  test -d "$am__dir" || /Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/build-aux/install-sh -c -d "$am__dir" || exit 1; \
	  emacs --batch \
	      \
	    $am__subdir_includes -L . -L /Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder \
	    --eval '(if (boundp (quote byte-compile-dest-file-function)) (setq byte-compile-dest-file-function (lambda (_) "lib/emacs/autoconf-mode.elc")) (defun byte-compile-dest-file (_) "lib/emacs/autoconf-mode.elc") )' \
	    -f batch-byte-compile '/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/lib/emacs/autoconf-mode.el'; \
	else :; fi
/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/build-aux/install-sh -c -d bin
if test 'emacs' != no; then \
	  am__dir=. am__subdir_includes=''; \
	  case lib/emacs/autotest-mode.elc in */*) \
	    am__dir=`echo 'lib/emacs/autotest-mode.elc' | sed 's,/[^/]*$,,'`; \
	    am__subdir_includes="-L $am__dir -L /Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/$am__dir"; \
	  esac; \
	  test -d "$am__dir" || /Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/build-aux/install-sh -c -d "$am__dir" || exit 1; \
	  emacs --batch \
	      \
	    $am__subdir_includes -L . -L /Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder \
	    --eval '(if (boundp (quote byte-compile-dest-file-function)) (setq byte-compile-dest-file-function (lambda (_) "lib/emacs/autotest-mode.elc")) (defun byte-compile-dest-file (_) "lib/emacs/autotest-mode.elc") )' \
	    -f batch-byte-compile '/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/lib/emacs/autotest-mode.el'; \
	else :; fi
mkdir: bin: File exists
mkdir: lib: File exists
srcdir=''; \
	  test -f ./bin/autoheader.in || srcdir=/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/; \
	  sed -e 's|@SHELL[@]|/bin/sh|g' -e 's|@PERL[@]|/usr/bin/perl|g' -e 's|@PERL_FLOCK[@]|yes|g' -e 's|@bindir[@]|/Users/graeme/.conan/data/autoconf/2.71/_/_/package/a728acd332aea736fea687b754a5e13cc4bdbb22/bin|g' -e 's|@pkgdatadir[@]|/Users/graeme/.conan/data/autoconf/2.71/_/_/package/a728acd332aea736fea687b754a5e13cc4bdbb22/bin/share/autoconf|g' -e 's|@prefix[@]|/Users/graeme/.conan/data/autoconf/2.71/_/_/package/a728acd332aea736fea687b754a5e13cc4bdbb22|g' -e 's|@autoconf-name[@]|'`echo autoconf | sed 's,x,x,'`'|g' -e 's|@autoheader-name[@]|'`echo autoheader | sed 's,x,x,'`'|g' -e 's|@autom4te-name[@]|'`echo autom4te | sed 's,x,x,'`'|g' -e 's|@M4[@]|/usr/bin/env m4|g' -e 's|@M4_DEBUGFILE[@]|--error-output|g' -e 's|@M4_GNU[@]||g' -e 's|@AWK[@]|awk|g' -e 's|@RELEASE_YEAR[@]|2021|g' -e 's|@VERSION[@]|2.71|g' -e 's|@PACKAGE_NAME[@]|GNU Autoconf|g' -e 's|@configure_input[@]|Generated from bin/autoheader.in; do not edit by hand.|g' ${srcdir}bin/autoheader.in >bin/autoheader.tmp
sed -e 's|@SHELL[@]|/bin/sh|g' -e 's|@PERL[@]|/usr/bin/perl|g' -e 's|@PERL_FLOCK[@]|yes|g' -e 's|@bindir[@]|/Users/graeme/.conan/data/autoconf/2.71/_/_/package/a728acd332aea736fea687b754a5e13cc4bdbb22/bin|g' -e 's|@pkgdatadir[@]|/Users/graeme/.conan/data/autoconf/2.71/_/_/package/a728acd332aea736fea687b754a5e13cc4bdbb22/bin/share/autoconf|g' -e 's|@prefix[@]|/Users/graeme/.conan/data/autoconf/2.71/_/_/package/a728acd332aea736fea687b754a5e13cc4bdbb22|g' -e 's|@autoconf-name[@]|'`echo autoconf | sed 's,x,x,'`'|g' -e 's|@autoheader-name[@]|'`echo autoheader | sed 's,x,x,'`'|g' -e 's|@autom4te-name[@]|'`echo autom4te | sed 's,x,x,'`'|g' -e 's|@M4[@]|/usr/bin/env m4|g' -e 's|@M4_DEBUGFILE[@]|--error-output|g' -e 's|@M4_GNU[@]||g' -e 's|@AWK[@]|awk|g' -e 's|@RELEASE_YEAR[@]|2021|g' -e 's|@VERSION[@]|2.71|g' -e 's|@PACKAGE_NAME[@]|GNU Autoconf|g' -e 's|@configure_input[@]|Generated from lib/autom4te.cfg.in; do not edit by hand.|g' /Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/lib/autom4te.in >lib/autom4te.cfg-t
:;{ \
	  echo '# This file is part of -*- Autoconf -*-.' && \
	  echo '# Version of Autoconf.' && \
	  echo '# Copyright (C) 1999, 2000, 2001, 2002, 2006, 2007, 2009' && \
	  echo '# Free Software Foundation, Inc.' && \
	  echo  &&\
	  echo 'm4_define([m4_PACKAGE_NAME],      [GNU Autoconf])' && \
	  echo 'm4_define([m4_PACKAGE_TARNAME],   [autoconf])' && \
	  echo 'm4_define([m4_PACKAGE_VERSION],   [2.71])' && \
	  echo 'm4_define([m4_PACKAGE_STRING],    [GNU Autoconf 2.71])' && \
	  echo 'm4_define([m4_PACKAGE_BUGREPORT], [bug-autoconf@gnu.org])' && \
	  echo 'm4_define([m4_PACKAGE_URL],       [https://www.gnu.org/software/autoconf/])' && \
	  echo 'm4_define([m4_PACKAGE_YEAR],      [2021])'; \
	} > lib/m4sugar/version.m4-t
srcdir=''; \
	  test -f ./bin/autom4te.in || srcdir=/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/; \
	  sed -e 's|@SHELL[@]|/bin/sh|g' -e 's|@PERL[@]|/usr/bin/perl|g' -e 's|@PERL_FLOCK[@]|yes|g' -e 's|@bindir[@]|/Users/graeme/.conan/data/autoconf/2.71/_/_/package/a728acd332aea736fea687b754a5e13cc4bdbb22/bin|g' -e 's|@pkgdatadir[@]|/Users/graeme/.conan/data/autoconf/2.71/_/_/package/a728acd332aea736fea687b754a5e13cc4bdbb22/bin/share/autoconf|g' -e 's|@prefix[@]|/Users/graeme/.conan/data/autoconf/2.71/_/_/package/a728acd332aea736fea687b754a5e13cc4bdbb22|g' -e 's|@autoconf-name[@]|'`echo autoconf | sed 's,x,x,'`'|g' -e 's|@autoheader-name[@]|'`echo autoheader | sed 's,x,x,'`'|g' -e 's|@autom4te-name[@]|'`echo autom4te | sed 's,x,x,'`'|g' -e 's|@M4[@]|/usr/bin/env m4|g' -e 's|@M4_DEBUGFILE[@]|--error-output|g' -e 's|@M4_GNU[@]||g' -e 's|@AWK[@]|awk|g' -e 's|@RELEASE_YEAR[@]|2021|g' -e 's|@VERSION[@]|2.71|g' -e 's|@PACKAGE_NAME[@]|GNU Autoconf|g' -e 's|@configure_input[@]|Generated from bin/autom4te.in; do not edit by hand.|g' ${srcdir}bin/autom4te.in >bin/autom4te.tmp
mv lib/m4sugar/version.m4-t lib/m4sugar/version.m4
srcdir=''; \
	  test -f ./bin/autoupdate.in || srcdir=/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/; \
	  sed -e 's|@SHELL[@]|/bin/sh|g' -e 's|@PERL[@]|/usr/bin/perl|g' -e 's|@PERL_FLOCK[@]|yes|g' -e 's|@bindir[@]|/Users/graeme/.conan/data/autoconf/2.71/_/_/package/a728acd332aea736fea687b754a5e13cc4bdbb22/bin|g' -e 's|@pkgdatadir[@]|/Users/graeme/.conan/data/autoconf/2.71/_/_/package/a728acd332aea736fea687b754a5e13cc4bdbb22/bin/share/autoconf|g' -e 's|@prefix[@]|/Users/graeme/.conan/data/autoconf/2.71/_/_/package/a728acd332aea736fea687b754a5e13cc4bdbb22|g' -e 's|@autoconf-name[@]|'`echo autoconf | sed 's,x,x,'`'|g' -e 's|@autoheader-name[@]|'`echo autoheader | sed 's,x,x,'`'|g' -e 's|@autom4te-name[@]|'`echo autom4te | sed 's,x,x,'`'|g' -e 's|@M4[@]|/usr/bin/env m4|g' -e 's|@M4_DEBUGFILE[@]|--error-output|g' -e 's|@M4_GNU[@]||g' -e 's|@AWK[@]|awk|g' -e 's|@RELEASE_YEAR[@]|2021|g' -e 's|@VERSION[@]|2.71|g' -e 's|@PACKAGE_NAME[@]|GNU Autoconf|g' -e 's|@configure_input[@]|Generated from bin/autoupdate.in; do not edit by hand.|g' ${srcdir}bin/autoupdate.in >bin/autoupdate.tmp
srcdir=''; \
	  test -f ./bin/autoscan.in || srcdir=/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/; \
	  sed -e 's|@SHELL[@]|/bin/sh|g' -e 's|@PERL[@]|/usr/bin/perl|g' -e 's|@PERL_FLOCK[@]|yes|g' -e 's|@bindir[@]|/Users/graeme/.conan/data/autoconf/2.71/_/_/package/a728acd332aea736fea687b754a5e13cc4bdbb22/bin|g' -e 's|@pkgdatadir[@]|/Users/graeme/.conan/data/autoconf/2.71/_/_/package/a728acd332aea736fea687b754a5e13cc4bdbb22/bin/share/autoconf|g' -e 's|@prefix[@]|/Users/graeme/.conan/data/autoconf/2.71/_/_/package/a728acd332aea736fea687b754a5e13cc4bdbb22|g' -e 's|@autoconf-name[@]|'`echo autoconf | sed 's,x,x,'`'|g' -e 's|@autoheader-name[@]|'`echo autoheader | sed 's,x,x,'`'|g' -e 's|@autom4te-name[@]|'`echo autom4te | sed 's,x,x,'`'|g' -e 's|@M4[@]|/usr/bin/env m4|g' -e 's|@M4_DEBUGFILE[@]|--error-output|g' -e 's|@M4_GNU[@]||g' -e 's|@AWK[@]|awk|g' -e 's|@RELEASE_YEAR[@]|2021|g' -e 's|@VERSION[@]|2.71|g' -e 's|@PACKAGE_NAME[@]|GNU Autoconf|g' -e 's|@configure_input[@]|Generated from bin/autoscan.in; do not edit by hand.|g' ${srcdir}bin/autoscan.in >bin/autoscan.tmp
srcdir=''; \
	  test -f ./bin/autoreconf.in || srcdir=/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/; \
	  sed -e 's|@SHELL[@]|/bin/sh|g' -e 's|@PERL[@]|/usr/bin/perl|g' -e 's|@PERL_FLOCK[@]|yes|g' -e 's|@bindir[@]|/Users/graeme/.conan/data/autoconf/2.71/_/_/package/a728acd332aea736fea687b754a5e13cc4bdbb22/bin|g' -e 's|@pkgdatadir[@]|/Users/graeme/.conan/data/autoconf/2.71/_/_/package/a728acd332aea736fea687b754a5e13cc4bdbb22/bin/share/autoconf|g' -e 's|@prefix[@]|/Users/graeme/.conan/data/autoconf/2.71/_/_/package/a728acd332aea736fea687b754a5e13cc4bdbb22|g' -e 's|@autoconf-name[@]|'`echo autoconf | sed 's,x,x,'`'|g' -e 's|@autoheader-name[@]|'`echo autoheader | sed 's,x,x,'`'|g' -e 's|@autom4te-name[@]|'`echo autom4te | sed 's,x,x,'`'|g' -e 's|@M4[@]|/usr/bin/env m4|g' -e 's|@M4_DEBUGFILE[@]|--error-output|g' -e 's|@M4_GNU[@]||g' -e 's|@AWK[@]|awk|g' -e 's|@RELEASE_YEAR[@]|2021|g' -e 's|@VERSION[@]|2.71|g' -e 's|@PACKAGE_NAME[@]|GNU Autoconf|g' -e 's|@configure_input[@]|Generated from bin/autoreconf.in; do not edit by hand.|g' ${srcdir}bin/autoreconf.in >bin/autoreconf.tmp
chmod a-w lib/autom4te.cfg-t
chmod +x bin/autoheader.tmp
mv -f lib/autom4te.cfg-t lib/autom4te.cfg
chmod a-w bin/autoheader.tmp
chmod +x bin/autom4te.tmp
mv bin/autoheader.tmp bin/autoheader
chmod a-w bin/autom4te.tmp
mv bin/autom4te.tmp bin/autom4te
AUTOM4TE_PERLLIBDIR='/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder'/lib AUTOM4TE_CFG='lib/autom4te.cfg'         bin/autom4te -B ''lib -B '/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder'/lib         --language M4sh --cache '' \
	  --melt /Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/bin/autoconf.as -o bin/autoconf.in
chmod +x bin/autoreconf.tmp
chmod +x bin/autoscan.tmp
chmod +x bin/autoupdate.tmp
chmod a-w bin/autoreconf.tmp
chmod a-w bin/autoscan.tmp
chmod a-w bin/autoupdate.tmp
mv bin/autoreconf.tmp bin/autoreconf
mv bin/autoscan.tmp bin/autoscan
mv bin/autoupdate.tmp bin/autoupdate
AUTOM4TE_PERLLIBDIR='/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder'/lib AUTOM4TE_CFG='lib/autom4te.cfg'         bin/autom4te -B ''lib -B '/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder'/lib         --language=M4sh /Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/tests/wrapper.as -o tests/wrapper.in
/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/build-aux/install-sh -c -d lib/autoconf
/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/build-aux/install-sh -c -d lib/autoscan
/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/build-aux/install-sh -c -d lib/autotest
/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/build-aux/install-sh -c -d lib/m4sugar
/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/build-aux/install-sh -c -d lib/m4sugar
lang=`echo 'lib/m4sugar/m4sugar' | sed 's,.*/,,'` \
	  && if test $lang = autoconf; then \
	       lang=autoconf-without-aclocal-m4; \
	     else :; fi \
	  && AUTOM4TE_PERLLIBDIR='/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder'/lib AUTOM4TE_CFG='lib/autom4te.cfg'         bin/autom4te -B ''lib -B '/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder'/lib         \
		--language=$lang \
		--freeze \
		--output=lib/m4sugar/m4sugar.m4f
lang=`echo 'lib/m4sugar/m4sh' | sed 's,.*/,,'` \
	  && if test $lang = autoconf; then \
	       lang=autoconf-without-aclocal-m4; \
	     else :; fi \
	  && AUTOM4TE_PERLLIBDIR='/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder'/lib AUTOM4TE_CFG='lib/autom4te.cfg'         bin/autom4te -B ''lib -B '/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder'/lib         \
		--language=$lang \
		--freeze \
		--output=lib/m4sugar/m4sh.m4f
lang=`echo 'lib/autoconf/autoconf' | sed 's,.*/,,'` \
	  && if test $lang = autoconf; then \
	       lang=autoconf-without-aclocal-m4; \
	     else :; fi \
	  && AUTOM4TE_PERLLIBDIR='/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder'/lib AUTOM4TE_CFG='lib/autom4te.cfg'         bin/autom4te -B ''lib -B '/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder'/lib         \
		--language=$lang \
		--freeze \
		--output=lib/autoconf/autoconf.m4f
echo '# Automatically Generated: do not edit this file' >lib/autoscan/autoscan.list
sed '/^[#]/!q' /Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/lib/autoscan/autoscan.pre >>lib/autoscan/autoscan.list
lang=`echo 'lib/autotest/autotest' | sed 's,.*/,,'` \
	  && if test $lang = autoconf; then \
	       lang=autoconf-without-aclocal-m4; \
	     else :; fi \
	  && AUTOM4TE_PERLLIBDIR='/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder'/lib AUTOM4TE_CFG='lib/autom4te.cfg'         bin/autom4te -B ''lib -B '/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder'/lib         \
		--language=$lang \
		--freeze \
		--output=lib/autotest/autotest.m4f
( \
	  sed -n '/^[^#]/p' /Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/lib/autoscan/autoscan.pre; \
	  AUTOM4TE_PERLLIBDIR='/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder'/lib AUTOM4TE_CFG='lib/autom4te.cfg'         bin/autom4te -B ''lib -B '/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder'/lib         --cache '' -M -l autoconf-without-aclocal-m4 \
	    -t'AN_OUTPUT:$1: $2		$3' \
	) | LC_ALL=C sort >>lib/autoscan/autoscan.list
srcdir=''; \
	  test -f ./bin/ifnames.in || srcdir=/Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22/source_subfolder/; \
	  sed -e 's|@SHELL[@]|/bin/sh|g' -e 's|@PERL[@]|/usr/bin/perl|g' -e 's|@PERL_FLOCK[@]|yes|g' -e 's|@bindir[@]|/Users/graeme/.conan/data/autoconf/2.71/_/_/package/a728acd332aea736fea687b754a5e13cc4bdbb22/bin|g' -e 's|@pkgdatadir[@]|/Users/graeme/.conan/data/autoconf/2.71/_/_/package/a728acd332aea736fea687b754a5e13cc4bdbb22/bin/share/autoconf|g' -e 's|@prefix[@]|/Users/graeme/.conan/data/autoconf/2.71/_/_/package/a728acd332aea736fea687b754a5e13cc4bdbb22|g' -e 's|@autoconf-name[@]|'`echo autoconf | sed 's,x,x,'`'|g' -e 's|@autoheader-name[@]|'`echo autoheader | sed 's,x,x,'`'|g' -e 's|@autom4te-name[@]|'`echo autom4te | sed 's,x,x,'`'|g' -e 's|@M4[@]|/usr/bin/env m4|g' -e 's|@M4_DEBUGFILE[@]|--error-output|g' -e 's|@M4_GNU[@]||g' -e 's|@AWK[@]|awk|g' -e 's|@RELEASE_YEAR[@]|2021|g' -e 's|@VERSION[@]|2.71|g' -e 's|@PACKAGE_NAME[@]|GNU Autoconf|g' -e 's|@configure_input[@]|Generated from bin/ifnames.in; do not edit by hand.|g' ${srcdir}bin/ifnames.in >bin/ifnames.tmp
chmod +x bin/ifnames.tmp
chmod a-w bin/ifnames.tmp
mv bin/ifnames.tmp bin/ifnames
mkdir: lib/emacs: File exists
Warning (bytecomp): Changing `byte-compile-dest-file' is obsolete (as of 23.2);
set `byte-compile-dest-file-function' instead.
Warning (bytecomp): Changing `byte-compile-dest-file' is obsolete (as of 23.2);
set `byte-compile-dest-file-function' instead.
autom4te: error: need GNU m4 1.4 or later: /usr/bin/env m4
autom4te: error: need GNU m4 1.4 or later: /usr/bin/env m4
autom4te: error: need GNU m4 1.4 or later: /usr/bin/env m4
autom4te: error: need GNU m4 1.4 or later: /usr/bin/env m4
autom4te: error: need GNU m4 1.4 or later: /usr/bin/env m4
autom4te: error: need GNU m4 1.4 or later: /usr/bin/env m4
autom4te: error: need GNU m4 1.4 or later: /usr/bin/env m4
make[1]: *** [bin/autoconf.in] Error 1
make[1]: *** Waiting for unfinished jobs....
make[1]: *** [lib/m4sugar/m4sh.m4f] Error 1
make[1]: *** [lib/m4sugar/m4sugar.m4f] Error 1
make[1]: *** [tests/wrapper.in] Error 1
make[1]: *** [lib/autotest/autotest.m4f] Error 1
make[1]: *** [lib/autoconf/autoconf.m4f] Error 1
make: *** [all] Error 2
autoconf/2.71:
autoconf/2.71: ERROR: Package 'a728acd332aea736fea687b754a5e13cc4bdbb22' build failed
autoconf/2.71: WARN: Build folder /Users/graeme/.conan/data/autoconf/2.71/_/_/build/a728acd332aea736fea687b754a5e13cc4bdbb22
ERROR: autoconf/2.71: Error in build() method, line 68
	autotools.make()
	ConanException: Error 2 while executing make -j12
```
</details>
