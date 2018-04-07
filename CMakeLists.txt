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
set(3RD_PARTY_DIR ${CMAKE_CURRENT_LIST_DIR}/3rdparty)

set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)

set(SHOCK_SRC_C
        ${SRC_DIR}/AI.C
        ${SRC_DIR}/AIRUPT.C
        ${SRC_DIR}/AMAPLOOP.C
        ${SRC_DIR}/AMMOMFD.C
        ${SRC_DIR}/AUTOMAP.C
        ${SRC_DIR}/BARK.C
        ${SRC_DIR}/BIOHELP.C
        ${SRC_DIR}/CARDMFD.C
        ${SRC_DIR}/CITRES.C
        ${SRC_DIR}/COMBAT.C
        ${SRC_DIR}/CONE.C
        ${SRC_DIR}/CRITERR.C
        ${SRC_DIR}/CYBER.C
        ${SRC_DIR}/CYBERMFD.C
        ${SRC_DIR}/CYBRND.C
        ${SRC_DIR}/DAMAGE.C
        ${SRC_DIR}/DIGIFX.C
        ${SRC_DIR}/DRUGS.C
        ${SRC_DIR}/EFFECT.C
        ${SRC_DIR}/EMAIL.C
        ${SRC_DIR}/FACEOBJ.C
        ${SRC_DIR}/FIXTRMFD.C
        ${SRC_DIR}/FRCAMERA.C
        ${SRC_DIR}/FRCLIP.C
        ${SRC_DIR}/FRCOMPIL.C
        ${SRC_DIR}/FRMAIN.C
        ${SRC_DIR}/FROBJ.C
        ${SRC_DIR}/FROSLEW.C
        ${SRC_DIR}/FRPIPE.C
        ${SRC_DIR}/FRPTS.C
        ${SRC_DIR}/FRSETUP.C
        ${SRC_DIR}/FRTABLES.C
        ${SRC_DIR}/FRTERR.C
        ${SRC_DIR}/FRUTIL.C
        ${SRC_DIR}/FrUtils.C
        ${SRC_DIR}/FULLAMAP.C
        ${SRC_DIR}/FULLSCRN.C
        ${SRC_DIR}/GAMELOOP.C
        ${SRC_DIR}/GAMEOBJ.C
        ${SRC_DIR}/GAMEREND.C
        ${SRC_DIR}/GAMESORT.C
        ${SRC_DIR}/GAMESTRN.C
        ${SRC_DIR}/GAMESYS.C
        ${SRC_DIR}/GAMETIME.C
        ${SRC_DIR}/GAMEWRAP.C
        ${SRC_DIR}/GEARMFD.C
        ${SRC_DIR}/GR2SS.C
        ${SRC_DIR}/GRENADES.C
        ${SRC_DIR}/HAND.C
        ${SRC_DIR}/HFLIP.C
        ${SRC_DIR}/HKEYFUNC.C
        ${SRC_DIR}/HUD.C
        ${SRC_DIR}/HUDOBJ.C
        ${SRC_DIR}/INIT.C
        ${SRC_DIR}/INPUT.C
        ${SRC_DIR}/INVENT.C
        ${SRC_DIR}/LEANMETR.C
        ${SRC_DIR}/MAINLOOP.C
        ${SRC_DIR}/MAP.C
        ${SRC_DIR}/MFDFUNC.C
        ${SRC_DIR}/MFDGADG.C
        ${SRC_DIR}/MFDGAMES.C
        ${SRC_DIR}/MFDGUMP.C
        ${SRC_DIR}/MFDPANEL.C
        ${SRC_DIR}/MINIMAX.C
        ${SRC_DIR}/MLIMBS.C
        ${SRC_DIR}/MOVEKEYS.C
        ${SRC_DIR}/MUSICAI.C
        ${SRC_DIR}/NEWAI.C
        ${SRC_DIR}/NEWMFD.C
        ${SRC_DIR}/OBJAPP.C
        ${SRC_DIR}/OBJECTS.C
        ${SRC_DIR}/OBJPROP.C
        ${SRC_DIR}/OBJSIM.C
        ${SRC_DIR}/OBJUSE.C
        ${SRC_DIR}/OLH.C
        ${SRC_DIR}/OLHSCAN.C
        ${SRC_DIR}/PALFX.C
        ${SRC_DIR}/PATHFIND.C
        ${SRC_DIR}/PHYSICS.C
        ${SRC_DIR}/PLAYER.C
        ${SRC_DIR}/PLOTWARE.C
        ${SRC_DIR}/POPUPS.C
        ${SRC_DIR}/RENDER.C
        ${SRC_DIR}/RENDTOOL.C
        ${SRC_DIR}/SAVELOAD.C
        ${SRC_DIR}/SCHEDULE.C
        ${SRC_DIR}/SCREEN.C
        ${SRC_DIR}/SETUP.C
        ${SRC_DIR}/SHODAN.C
        ${SRC_DIR}/SIDEICON.C
        ${SRC_DIR}/SNDCALL.C
        ${SRC_DIR}/STAR.C
        ${SRC_DIR}/STATICS.C
        ${SRC_DIR}/STATUS.C
        ${SRC_DIR}/TARGET.C
        ${SRC_DIR}/TEXTMAPS.C
        ${SRC_DIR}/TFDIRECT.C
        ${SRC_DIR}/TFUTIL.C
        ${SRC_DIR}/TOOLS.C
        ${SRC_DIR}/TRIGGER.C
        ${SRC_DIR}/VIEW360.C
        ${SRC_DIR}/VIEWHELP.C
        ${SRC_DIR}/VITALS.C
        ${SRC_DIR}/VMAIL.C
        ${SRC_DIR}/WARES.C
        ${SRC_DIR}/WEAPONS.C
        ${SRC_DIR}/WRAPPER.C)

add_executable(SystemShock ${SHOCK_SRC_C})

include_directories(SYSTEM ${SRC_DIR}/Headers)