cmake_minimum_required(VERSION 3.5...4.2.1 FATAL_ERROR)

add_definitions(-DCHECK_XDUKE_REV)

set(GAME_HEADER_FILES
	src/_functio.h
	src/_rts.h
	src/animlib.h
	src/config.h
	src/console.h
	src/control.h
	src/cvar_defs.h
	src/cvars.h
	src/develop.h
	src/duke3d.h
	src/dukeunix.h
	src/dukewin.h
	src/file_lib.h
	src/funct.h
	src/function.h
	src/game.h
	src/gamedefs.h
	src/global.h
	src/joystick.h
	src/keyboard.h
	src/mouse.h
	src/names.h
	src/premap.h
	src/rts.h
	src/scriplib.h
	src/sounddebugdefs.h
	src/soundefs.h
	src/sounds.h
	src/types.h
	src/util_lib.h
	src/audiolib/_multivc.h
	src/audiolib/dpmi.h
	src/audiolib/dsl.h
	src/audiolib/fx_man.h
	src/audiolib/linklist.h
	src/audiolib/ll_man.h
	src/audiolib/multivoc.h
	src/audiolib/music.h
	src/audiolib/pitch.h
	src/audiolib/sndcards.h
	src/audiolib/usrhooks.h
	src/audiolib/util.h
)

set(GAME_SOURCE_FILES
	src/actors.c
	src/animlib.c
	src/config.c
	src/console.c
	src/control.c
	src/cvar_defs.c
	src/cvars.c
	src/game.c
	src/gamedef.c
	src/global.c
	src/keyboard.c
	src/menues.c
	src/player.c
	src/premap.c
	src/rts.c
	src/scriplib.c
	src/sector.c
	src/sounds.c
	src/audiolib/dpmi.c
	src/audiolib/dsl.c
	src/audiolib/fx_man.c
	src/audiolib/ll_man.c
	src/audiolib/multivoc.c
	src/audiolib/mv_mix.c
	src/audiolib/mvreverb.c
	src/audiolib/pitch.c
	src/midi/sdl_midi.c
)

if(WIN32)
	set(GAME_RESOURCE_FILES chocolateDukeResources.rc)
	set(GAME_SOCKET_LIBRARY ws2_32.lib)
endif()

add_executable(Game ${GAME_SOURCE_FILES} ${GAME_HEADER_FILES} ${GAME_RESOURCE_FILES})

target_include_directories(Game PUBLIC "src")

target_link_libraries(Game
	PRIVATE
		Engine
		${GAME_SOCKET_LIBRARY}
)
