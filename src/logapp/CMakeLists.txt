SET(LOGAPPBIN_SRCS
	api.cpp
	db_task.cpp
	dboper.cpp
	http.cpp
	main.cpp
	other.cpp
	threadpool.cpp
	world_other.cpp
)


include_directories(
	./
	../common/
	../base/
	../cell/
)

add_executable(logapp
    ${LOGAPPBIN_SRCS}
)

TARGET_LINK_LIBRARIES(logapp "common")
TARGET_LINK_LIBRARIES(logapp "tinyxml2")
TARGET_LINK_LIBRARIES(logapp "ssl")
TARGET_LINK_LIBRARIES(logapp "crypto")
TARGET_LINK_LIBRARIES(logapp "lua.5.2.4")
TARGET_LINK_LIBRARIES(logapp "boost_regex")
TARGET_LINK_LIBRARIES(logapp "mysqlclient")
TARGET_LINK_LIBRARIES(logapp "curl")


set_target_properties(logapp PROPERTIES
    OUTPUT_NAME "logapp"
    CLEAN_DIRECT_OUTPUT 1
    VERSION ${DARKSERVER_VERSION}
)

set_target_properties(logapp PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)
set_target_properties(logapp PROPERTIES RUNTIME_OUTPUT_DIRECTORY_DEBUG ${CMAKE_SOURCE_DIR}/bin)
set_target_properties(logapp PROPERTIES RUNTIME_OUTPUT_DIRECTORY_RELEASE ${CMAKE_SOURCE_DIR}/bin)