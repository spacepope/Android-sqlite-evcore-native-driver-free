# Android-sqlite-evcore-native-driver-free

Provides a native build of sqlite with a low-level API for Cordova sqlite enterprise versions.

Based on [liteglue / Android-sqlite-native-driver](https://github.com/liteglue/Android-sqlite-native-driver).

by Christopher J. Brody aka Chris Brody mailto: brodybits@litehelpers.net

License: GPL v3 (http://www.gnu.org/licenses/gpl.txt) or commercial license options

Includes JSMN (http://zserge.com/jsmn.html) under the MIT license

## About

Android-sqlite-evcore-native-driver-free provides:
- single `EVCoreNativeDriver` class with native Java interface to the needed C functions
- automatic build for major Android targets (`armeabi`, `armeabi-v7a`, `x86`, `x86_64`) that is accessible from the native Java interface

This is accomplished by using [GlueGen](http://jogamp.org/gluegen/www/) around the C module.

**NOTE:** This project references the `gluegentools` and `sqlite-amalgamation` subprojects, which are resolved by: $ `make init` (as described below).

**WARNING:** The reference handles that are returned by the `EVCoreNativeDriver` library functions are raw C pointer values (with `0x100000000` added). If someone uses a reference handle that is not valid, or no longer valid with the `EVCoreNativeDriver` library the behavior is undefined (may crash, for example). It is *NOT* recommended to use this API directly unless you really understand how this library works internally.

## SQLite build information

**SQLite version:** `3.15.2`

**SQLite build flags:**
- `-DSQLITE_TEMP_STORE=2`
- `-DSQLITE_THREADSAFE=2`
- `-DSQLITE_ENABLE_FTS3`
- `-DSQLITE_ENABLE_FTS3_PARENTHESIS`
- `-DSQLITE_ENABLE_FTS4`
- `-DSQLITE_ENABLE_RTREE`

**NOTE:** No default page/cache size is defined, newer default values are described at <http://sqlite.org/pgszchng2016.html>.

## Dependencies

- JSMN (MIT license)
- SQLite (public domain)

## Major TODO(s)

- Support BLOB type

# Building

## Normal build

Initialize with the `gluegentools` and `sqlite-amalgamation` subprojects:

$ `make init`

Then to build:

$ `make`

## Regenerage Java & C glue code

$ `make regen`
