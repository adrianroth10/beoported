cmake_minimum_required(VERSION 3.10)
project(beoported LANGUAGES CXX)

set(CMAKE_BUILD_TYPE Debug)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

add_subdirectory(libpc2 EXCLUDE_FROM_ALL)

###
# Boost
###

# set(Boost_ADDITIONAL_VERSIONS "1.67" "1.67.0")
# find_package(Boost 1.67 REQUIRED COMPONENTS log iostreams system thread)
# add_definitions(-DBOOST_LOG_DYN_LINK)

###

add_executable(beoported main.cpp notify.cpp)

target_include_directories(beoported PUBLIC .)
target_link_libraries(beoported pc2)
# target_link_libraries(beoported Boost::log)

find_package(PkgConfig REQUIRED)
pkg_check_modules(NOTIFY REQUIRED libusb-1.0)
pkg_check_modules(USB REQUIRED libnotify)

target_include_directories(beoported PUBLIC ${USB_INCLUDE_DIRS})
target_include_directories(beoported PUBLIC ${NOTIFY_INCLUDE_DIRS})
target_link_libraries(beoported ${USB_LINK_LIBRARIES})
target_link_libraries(beoported ${NOTIFY_LINK_LIBRARIES})
