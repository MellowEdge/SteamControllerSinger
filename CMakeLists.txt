cmake_minimum_required(VERSION 3.13)
project(SteamCS)

set(CMAKE_CXX_STANDARD 11)
add_executable(SteamCS main.cpp midifile/midifile.c midifile/midifile.h libusb/libusb.h)

find_library(LIBUSB_1_LIBRARY libusb-1.0 libusb)
target_link_libraries(SteamCS LINK_PUBLIC ${LIBUSB_1_LIBRARY} -static)