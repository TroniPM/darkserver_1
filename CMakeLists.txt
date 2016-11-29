cmake_minimum_required(VERSION 2.8)

project(DarkServer)

set(DARKSERVER_VERSION 1.0.0)
set(CMAKE_C_COMPILER_INIT g++)

# debug
message( "CMAKE_BUILD_TYPE: ${CMAKE_BUILD_TYPE}" )
if ( "${CMAKE_BUILD_TYPE}" STREQUAL "DEBUG" )
    add_definitions(-D_DEBUG)
endif()

# architecture
if ( CMAKE_SIZEOF_VOID_P EQUAL 8 )
set(ARCH_DIR "x64")
else()
set(ARCH_DIR "x86")
endif()


if ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "Clang")
    # using Clang
    add_definitions(-std=c++11 -stdlib=libc++)
else()
    add_definitions(-std=c++11)
    add_definitions(-lstdc++)
endif()


# __LUA_5_2_1
add_definitions(-D__LUA_5_2_1)
# __RELOGIN
add_definitions(-D__RELOGIN)



include_directories(
	/usr/local/include/
	/usr/local/include/mysql/
	/usr/local/opt/openssl/include/
	/usr/local/include/luajit-2.1/
)

SET (EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin)
SET (LIBRARY_OUTPUT_PATH ${PROJECT_BINARY_DIR}/lib)


link_directories(
	${PROJECT_BINARY_DIR}/lib
	/usr/local/lib/
	/usr/local/opt/curl/lib/
	/usr/local/opt/openssl/lib/
)


# common library
add_subdirectory(src/common)

# base
add_subdirectory(src/base)

# cell
add_subdirectory(src/cell)

# cwmd
add_subdirectory(src/cwmd)

# dbmgr
add_subdirectory(src/dbmgr)

# logapp
add_subdirectory(src/logapp)

# loginapp
add_subdirectory(src/loginapp)

# syncdb
add_subdirectory(src/syncdb)

# timerd
add_subdirectory(src/timerd)


