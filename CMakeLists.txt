cmake_minimum_required(VERSION 3.8)
project(systemshock)

# Initialize cmake options
set(CMAKE_MODULE_PATH "${CMAKE_CURRENT_LIST_DIR}/cmake")
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS}")
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})
# set(CMAKE_BUILD_TYPE RELEASE)

set(CMAKE_INSTALL_PREFIX ${CMAKE_CURRENT_LIST_DIR})

set(SRC_DIR "${CMAKE_CURRENT_LIST_DIR}/ShockMac/Game Src")
set(3RD_PARTY_DIR ${SRC_DIR}/../Libraries)

include_directories(SYSTEM ${SRC_DIR}/Headers)

set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)

enable_language(ASM)

add_subdirectory(${3RD_PARTY_DIR}/2D)

set(SHOCK_SRC_C
        ${SRC_DIR}/ai.c
        ${SRC_DIR}/airupt.c
        ${SRC_DIR}/amap.c
        ${SRC_DIR}/amaploop.c
        ${SRC_DIR}/ammomfd.c
        ${SRC_DIR}/audiolog.c
        ${SRC_DIR}/automap.c
        ${SRC_DIR}/bark.c
        ${SRC_DIR}/biohelp.c
        ${SRC_DIR}/cardmfd.c
        ${SRC_DIR}/citres.c
        ${SRC_DIR}/combat.c
        ${SRC_DIR}/cone.c
        ${SRC_DIR}/criterr.c
        ${SRC_DIR}/cyber.c
        ${SRC_DIR}/cybermfd.c
        ${SRC_DIR}/cybmem.c
        ${SRC_DIR}/cybrnd.c
        ${SRC_DIR}/damage.c
        ${SRC_DIR}/digifx.c
        ${SRC_DIR}/drugs.c
        ${SRC_DIR}/effect.c
        ${SRC_DIR}/email.c
        ${SRC_DIR}/faceobj.c
        ${SRC_DIR}/fixtrmfd.c
        ${SRC_DIR}/frcamera.c
        ${SRC_DIR}/frclip.c
        ${SRC_DIR}/frcompil.c
        ${SRC_DIR}/frmain.c
        ${SRC_DIR}/frobj.c
        ${SRC_DIR}/froslew.c
        ${SRC_DIR}/frpipe.c
        ${SRC_DIR}/frpts.c
        ${SRC_DIR}/frsetup.c
        ${SRC_DIR}/frtables.c
        ${SRC_DIR}/frterr.c
        ${SRC_DIR}/frutil.c
        ${SRC_DIR}/frutils.c
        ${SRC_DIR}/fullamap.c
        ${SRC_DIR}/fullscrn.c
        ${SRC_DIR}/gameloop.c
        ${SRC_DIR}/gameobj.c
        ${SRC_DIR}/gamerend.c
        ${SRC_DIR}/gamesort.c
        ${SRC_DIR}/gamestrn.c
        ${SRC_DIR}/gamesys.c
        ${SRC_DIR}/gametime.c
        ${SRC_DIR}/gamewrap.c
        ${SRC_DIR}/gearmfd.c
        ${SRC_DIR}/gr2ss.c
        ${SRC_DIR}/grenades.c
        ${SRC_DIR}/hand.c
        ${SRC_DIR}/hflip.c
        ${SRC_DIR}/hkeyfunc.c
        ${SRC_DIR}/hud.c
        ${SRC_DIR}/hudobj.c
        ${SRC_DIR}/init.c
        ${SRC_DIR}/input.c
        ${SRC_DIR}/invent.c
        ${SRC_DIR}/leanmetr.c
        ${SRC_DIR}/mainloop.c
        ${SRC_DIR}/map.c
        ${SRC_DIR}/mfdfunc.c
        ${SRC_DIR}/mfdgadg.c
        ${SRC_DIR}/mfdgames.c
        ${SRC_DIR}/mfdgump.c
        ${SRC_DIR}/mfdpanel.c
        ${SRC_DIR}/minimax.c
        ${SRC_DIR}/mlimbs.c
        ${SRC_DIR}/movekeys.c
        ${SRC_DIR}/musicai.c
        ${SRC_DIR}/newai.c
        ${SRC_DIR}/newmfd.c
        ${SRC_DIR}/objapp.c
        ${SRC_DIR}/objects.c
        ${SRC_DIR}/objload.c
        ${SRC_DIR}/objprop.c
        ${SRC_DIR}/objsim.c
        ${SRC_DIR}/objuse.c
        ${SRC_DIR}/olh.c
        ${SRC_DIR}/olhscan.c
        ${SRC_DIR}/palfx.c
        ${SRC_DIR}/pathfind.c
        ${SRC_DIR}/physics.c
        ${SRC_DIR}/player.c
        ${SRC_DIR}/plotware.c
        ${SRC_DIR}/popups.c
        ${SRC_DIR}/render.c
        ${SRC_DIR}/rendtool.c
        ${SRC_DIR}/saveload.c
        ${SRC_DIR}/schedule.c
        ${SRC_DIR}/screen.c
        ${SRC_DIR}/setup.c
        ${SRC_DIR}/shodan.c
        ${SRC_DIR}/sideicon.c
        ${SRC_DIR}/sndcall.c
        ${SRC_DIR}/star.c
        ${SRC_DIR}/statics.c
        ${SRC_DIR}/status.c
        ${SRC_DIR}/target.c
        ${SRC_DIR}/textmaps.c
        ${SRC_DIR}/tfdirect.c
        ${SRC_DIR}/tfutil.c
        ${SRC_DIR}/tools.c
        ${SRC_DIR}/trigger.c
        ${SRC_DIR}/view360.c
        ${SRC_DIR}/viewhelp.c
        ${SRC_DIR}/vitals.c
        ${SRC_DIR}/vmail.c
        ${SRC_DIR}/wares.c
        ${SRC_DIR}/weapons.c
        ${SRC_DIR}/wrapper.c)

set(SHOCK_SRC_ASM
        ${SRC_DIR}/blitlargealign.s
        ${SRC_DIR}/clearcache.s
        )

add_executable(SystemShock ${SHOCK_SRC_C} ${SHOCK_SRC_ASM})