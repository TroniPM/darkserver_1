SET(DBMGRBIN_SRCS
	db_task.cpp
	dbmgr.cpp
	dboper.cpp
	myredis.cpp
	world_dbmgr.cpp
	main.cpp
)


include_directories(
	./
	../common/
	../base/
	../cell/
)

add_executable(dbmgr
    ${DBMGRBIN_SRCS}
)

TARGET_LINK_LIBRARIES(dbmgr "common")
TARGET_LINK_LIBRARIES(dbmgr "tinyxml2")
TARGET_LINK_LIBRARIES(dbmgr "ssl")
TARGET_LINK_LIBRARIES(dbmgr "crypto")
TARGET_LINK_LIBRARIES(dbmgr "lua.5.2.4")
TARGET_LINK_LIBRARIES(dbmgr "boost_regex")
TARGET_LINK_LIBRARIES(dbmgr "mysqlclient")
TARGET_LINK_LIBRARIES(dbmgr "hiredis")



set_target_properties(dbmgr PROPERTIES
    OUTPUT_NAME "dbmgr"
    CLEAN_DIRECT_OUTPUT 1
    VERSION ${DARKSERVER_VERSION}
)

