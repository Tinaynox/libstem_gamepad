project(libstem_gamepad)

if(${CMAKE_SYSTEM_NAME} STREQUAL "Windows")
add_library(libstem_gamepad STATIC source/gamepad/Gamepad_private.c source/gamepad/Gamepad_windows_dinput.c)
elseif(UNIX AND NOT APPLE)
add_library(libstem_gamepad STATIC source/gamepad/Gamepad_private.c source/gamepad/Gamepad_linux.c)
elseif(APPLE AND NOT IOS)
add_library(libstem_gamepad STATIC source/gamepad/Gamepad_private.c source/gamepad/Gamepad_macosx.c)
else()
message(FATAL_ERROR "Not supported platform")
endif()
	
target_include_directories(libstem_gamepad PUBLIC source)