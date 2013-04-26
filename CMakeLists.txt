# Copyright (C) 2007-2013 LuaDist.
# Created by Peter Drahoš, Peter Kapec
# Redistribution and use of this file is allowed according to the terms of the MIT license.
# For details see the COPYRIGHT file distributed with LuaDist.
# Please note that the package source code is licensed under its own license.

project ( libev C )
cmake_minimum_required ( VERSION 2.8 )
include ( cmake/dist.cmake )
include ( configure )

configure_file ( ${CMAKE_CURRENT_SOURCE_DIR}/config.h.cmake ${CMAKE_CURRENT_BINARY_DIR}/config.h )
include_directories( ${CMAKE_CURRENT_BINARY_DIR} )

set ( EV_SRC 
  ev.c
  event.c
)

if (WIN32) 
  list ( APPEND EV_SRC ev_win32.c )
endif ()

add_library ( ev ${EV_SRC} )

install_library ( ev )
install_header ( ev.h ev++.h event.h )
install_data ( LICENSE README )
