SET(LOGINAPPBIN_SRCS
	loginapp.cpp
	world_login.cpp
	main.cpp
)


include_directories(
	./
	../common/
	../base/
	../cell/
)

add_executable(loginapp
    ${LOGINAPPBIN_SRCS}
)

TARGET_LINK_LIBRARIES(loginapp "common")
TARGET_LINK_LIBRARIES(loginapp "ssl")
TARGET_LINK_LIBRARIES(loginapp "crypto")
TARGET_LINK_LIBRARIES(loginapp "lua")
TARGET_LINK_LIBRARIES(loginapp "boost_regex")
TARGET_LINK_LIBRARIES(loginapp "mysqlclient")


set_target_properties(loginapp PROPERTIES
    OUTPUT_NAME "loginapp"
    CLEAN_DIRECT_OUTPUT 1
    VERSION ${DARKSERVER_VERSION}
)

set_target_properties(loginapp PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)
set_target_properties(loginapp PROPERTIES RUNTIME_OUTPUT_DIRECTORY_DEBUG ${CMAKE_SOURCE_DIR}/bin)
set_target_properties(loginapp PROPERTIES RUNTIME_OUTPUT_DIRECTORY_RELEASE ${CMAKE_SOURCE_DIR}/bin)