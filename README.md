#  Boost 1.78.0 C++ Xcode

This example shows complication errors on a default iOS project when including
boost 1.78.0.

## Getting Boost

```sh
brew install boost
```

## Search Paths

These are already configured in the example `.xcodeproj` file. But here's the reference. 
It's possible your version of homebrew is configured for a different directory. Some older
posts suggest `/usr/local/include`. 

```
HEADER_SEARCH_PATHS = /opt/homebrew/include;
```

The same result also occurs when setting this directly to the boost installation include:

```
HEADER_SEARCH_PATHS = /opt/homebrew/Cellar/boost/1.78.0_1/include;
```

The issue is the same when library search paths are set as well.

```
LIBRARY_SEARCH_PATHS = /opt/homebrew/lib;
```

## Build Errors

These are just some samples. There are more that can be seen when building the project.

```log
In file included from ~/Desktop/Boost Test/Boost Test/Boost.m:10:
In file included from /opt/homebrew/include/boost/property_tree/ptree.hpp:15:
In file included from /opt/homebrew/include/boost/property_tree/ptree_fwd.hpp:15:
/opt/homebrew/include/boost/optional/optional_fwd.hpp:21:1: error: unknown type name 'namespace'
namespace boost {
^
/opt/homebrew/include/boost/optional/optional_fwd.hpp:21:16: error: expected ';' after top level declarator
namespace boost {
               ^
               ;
In file included from ~/Desktop/Boost Test/Boost Test/Boost.m:10:
In file included from /opt/homebrew/include/boost/property_tree/ptree.hpp:15:
In file included from /opt/homebrew/include/boost/property_tree/ptree_fwd.hpp:16:
In file included from /opt/homebrew/include/boost/throw_exception.hpp:23:
/opt/homebrew/include/boost/exception/exception.hpp:10:10: fatal error: 'exception' file not found
#include <exception>
         ^~~~~~~~~~~
3 errors generated.
```
