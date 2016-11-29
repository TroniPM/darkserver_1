SET(SYNCDBBIN_SRCS
	../dbmgr/world_dbmgr.cpp
	../dbmgr/dboper.cpp
	../dbmgr/db_task.cpp
	../dbmgr/dbmgr.cpp
	main.cpp
)


include_directories(
	./
	../common/
	../base/
	../cell/
	../cwmd/
	../dbmgr/
)

add_executable(syncdb
    ${SYNCDBBIN_SRCS}
)

TARGET_LINK_LIBRARIES(syncdb "common")
TARGET_LINK_LIBRARIES(syncdb "ssl")
TARGET_LINK_LIBRARIES(syncdb "crypto")
TARGET_LINK_LIBRARIES(syncdb "lua.5.2.4")
TARGET_LINK_LIBRARIES(syncdb "boost_regex")
TARGET_LINK_LIBRARIES(syncdb "mysqlclient")
TARGET_LINK_LIBRARIES(syncdb "hiredis")


set_target_properties(syncdb PROPERTIES
    OUTPUT_NAME "syncdb"
    CLEAN_DIRECT_OUTPUT 1
    VERSION ${DARKSERVER_VERSION}
)

set_target_properties(syncdb PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)
set_target_properties(syncdb PROPERTIES RUNTIME_OUTPUT_DIRECTORY_DEBUG ${CMAKE_SOURCE_DIR}/bin)
set_target_properties(syncdb PROPERTIES RUNTIME_OUTPUT_DIRECTORY_RELEASE ${CMAKE_SOURCE_DIR}/bin)