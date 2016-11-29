SET(BASE_SRCS
	../base/entity_base.cpp  
	../base/lua_base.cpp  
	../base/world_base.cpp
)

SET(CELL_SRCS
	../cell/entity_cell.cpp  
	../cell/aoi.cpp  
	../cell/lua_cell.cpp  
	../cell/space.cpp  
	../cell/world_cell.cpp
)

SET(COMMON_SRCS
	balance.cpp
	balance.h
	base64.cpp
	base64.h
	bitcryto.cpp
	bitcryto.h
	cfg_reader.cpp
	cfg_reader.h
	cjson.cpp
	cjson.h
	debug.cpp
	debug.h
	defparser.cpp
	defparser.h
	delegate.h
	entity.cpp
	entity.h
	entity_mgr.cpp
	entity_mgr.h
	epoll_server.cpp
	epoll_server.h
	event.h
	exception.cpp
	exception.h
	global_config.h
	json_helper.cpp
	json_helper.h
	logger.cpp
	logger.h
	lua_bitset.cpp
	lua_bitset.h
	lua_mogo.cpp
	lua_mogo.h
	lua_mogo_impl.h
	mailbox.cpp
	mailbox.h
	md5.cpp
	md5.h
	memory_pool.cpp
	memory_pool.h
	mutex.cpp
	mutex.h
	my_stl.h
	net_util.cpp
	net_util.h
	path_founder.cpp
	path_founder.h
	pluto.cpp
	pluto.h
	rpc_mogo.cpp
	rpc_mogo.h
	server_test.cpp
	stopword.cpp
	stopword.h
	timer.cpp
	timer.h
	timer_action.cpp
	timer_action.h
	type_mogo.cpp
	type_mogo.h
	util.cpp
	util.h
	win_adaptor.cpp
	win_adaptor.h
	world.cpp
	world.h
	world_select.h
	xmsg.cpp
	xmsg.h
	xsem.cpp
	xsem.h
	${BASE_SRCS}
	${CELL_SRCS}
)

include_directories(
	./
	../base/
	../cell/
)

add_library(common STATIC
    ${COMMON_SRCS}
)

set_target_properties(common PROPERTIES
    OUTPUT_NAME "common"
    CLEAN_DIRECT_OUTPUT 1
    VERSION ${DARKSERVER_VERSION}
)

