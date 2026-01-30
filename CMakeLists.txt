cmake_minimum_required(VERSION 3.5...4.2.1 FATAL_ERROR)

# set_property(GLOBAL PROPERTY USE_FOLDERS ON)
list(INSERT CMAKE_MODULE_PATH 0 ${CMAKE_CURRENT_SOURCE_DIR}/CMake)
set(ROOT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR} CACHE INTERNAL "" FORCE)

include(ConfigureCPlusPlus)
include(Hunter/HunterInit)

project(ChocolateDuke3D VERSION 1.0.0 LANGUAGES C CXX)

if(NOT (CMAKE_GENERATOR MATCHES "Visual Studio") AND NOT CMAKE_BUILD_TYPE)
	message(FATAL_ERROR "Must set 'CMAKE_BUILD_TYPE' for single configuration generators.")
endif()

if(MSVC)
	add_compile_options(
		/Zc:__cplusplus
		/Zc:preprocessor-
	)
endif()

if(WIN32)
	add_definitions(
		-DWIN32_LEAN_AND_MEAN
		-D_CRT_SECURE_NO_DEPRECATE
		-D_CRT_NONSTDC_NO_DEPRECATE
	)
elseif(UNIX)
	add_definitions(-DUNIX)
	add_compile_options(
		-Wall,
		-fno-strict-aliasing
		-fcommon
	)
endif()

add_subdirectory(Engine)
add_subdirectory(Game)

set_property(
	DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
	PROPERTY VS_STARTUP_PROJECT Game
)
