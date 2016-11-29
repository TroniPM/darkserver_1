SET(TIMERDBIN_SRCS
	timerd.cpp
	world_timerd.cpp
	main.cpp
)


include_directories(
	./
	../common/
	../base/
	../cell/
)

add_executable(timerd
    ${TIMERDBIN_SRCS}
)

TARGET_LINK_LIBRARIES(timerd "common")
TARGET_LINK_LIBRARIES(timerd "tinyxml2")
TARGET_LINK_LIBRARIES(timerd "ssl")
TARGET_LINK_LIBRARIES(timerd "crypto")
TARGET_LINK_LIBRARIES(timerd "lua.5.2.4")
TARGET_LINK_LIBRARIES(timerd "boost_regex")
TARGET_LINK_LIBRARIES(timerd "mysqlclient")


set_target_properties(timerd PROPERTIES
    OUTPUT_NAME "timerd"
    CLEAN_DIRECT_OUTPUT 1
    VERSION ${DARKSERVER_VERSION}
)

set_target_properties(timerd PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)
set_target_properties(timerd PROPERTIES RUNTIME_OUTPUT_DIRECTORY_DEBUG ${CMAKE_SOURCE_DIR}/bin)
set_target_properties(timerd PROPERTIES RUNTIME_OUTPUT_DIRECTORY_RELEASE ${CMAKE_SOURCE_DIR}/bin)