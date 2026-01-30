cmake_minimum_required(VERSION 3.5...4.2.1 FATAL_ERROR)

set(ENGINE_HEADER_FILES
	src/build.h
	src/cache.h
	src/display.h
	src/draw.h
	src/engine.h
	src/filesystem.h
	src/fixedPoint_math.h
	src/icon.h
	src/macos_compat.h
	src/mmulti.h
	src/platform.h
	src/sdl_util.h
	src/tiles.h
	src/unix_compat.h
	src/win32_compat.h
)

set(ENGINE_SOURCE_FILES
	src/cache.c
	src/display.c
	src/draw.c
	src/engine.c
	src/filesystem.c
	src/fixedPoint_math.c
	src/mmulti.c
	src/tiles.c
)

add_library(Engine STATIC ${ENGINE_SOURCE_FILES} ${ENGINE_HEADER_FILES})

target_include_directories(Engine PUBLIC "src")

# target_link_libraries(Engine PUBLIC ${SDL2_ALL_LIBRARIES})
