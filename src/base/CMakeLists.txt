SET(BASEBIN_SRCS
	baseapp.cpp  
	main.cpp
)


include_directories(
	./
	../common/
	../cell/
)

add_executable(baseapp
    ${BASEBIN_SRCS}
)

TARGET_LINK_LIBRARIES(baseapp "common")
TARGET_LINK_LIBRARIES(baseapp "ssl")
TARGET_LINK_LIBRARIES(baseapp "crypto")
TARGET_LINK_LIBRARIES(baseapp "lua.5.2.4")
TARGET_LINK_LIBRARIES(baseapp "boost_regex")
TARGET_LINK_LIBRARIES(baseapp "mysqlclient")


set_target_properties(baseapp PROPERTIES
    OUTPUT_NAME "baseapp"
    CLEAN_DIRECT_OUTPUT 1
    VERSION ${DARKSERVER_VERSION}
)


set_target_properties(baseapp PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)
set_target_properties(baseapp PROPERTIES RUNTIME_OUTPUT_DIRECTORY_DEBUG ${CMAKE_SOURCE_DIR}/bin)
set_target_properties(baseapp PROPERTIES RUNTIME_OUTPUT_DIRECTORY_RELEASE ${CMAKE_SOURCE_DIR}/bin)