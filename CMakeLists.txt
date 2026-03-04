cmake_minimum_required(VERSION 3.25.1)
project(dectalk)
set(CMAKE_C_STANDARD 90)
set(CMAKE_CXX_STANDARD 98)

option(BUILD_SAMPLES "Enables building the sample binaries. This requires GTK on Unix systems." ON)

# Set up the GNU install directories
include(GNUInstallDirs)

set(HEADER_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/headers)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

# Set up pkgconfig
find_package(PkgConfig REQUIRED)

# Initialise variables for "config.h" (to be injected into "config.h.cmakedefine")
if (NOT EMSCRIPTEN)
find_package(Iconv)
set(HAVE_ICONV Iconv_FOUND)
endif()
set(DECTALK_INSTALL_PREFIX "\"/opt/dectalk\"")
set(PACKAGE_BUGREPORT "\"https://github.com/dectalk/dectalk/issues\"")
set(PACKAGE_NAME "\"DECtalk\"")
set(PACKAGE_STRING "\"DECtalk\"")
set(PACKAGE_TARNAME "\"dectalk\"")
set(PACKAGE_URL "\"https://github.com/dectalk\"")
set(PACKAGE_VERSION "\"1.0.0\"")

add_subdirectory(src)
