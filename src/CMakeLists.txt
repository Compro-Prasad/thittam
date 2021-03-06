# Copyright (C) 2016-2017 HiPro IT Solutions Private Limited,
# Chennai. All rights reserved.
#
# This program and the accompanying materials are made available under
# the terms described in the LICENSE file which accompanies this
# distribution. If the LICENSE file was not attached to this
# distribution or for further clarifications, please contact
# legal@hipro.co.in.

set (CMAKE_CXX_FLAGS
  "${CMAKE_CXX_FLAGS} -std=gnu++1y -Wall -Werror")

add_library (app
  app_impl.cxx
  log.cxx
  common.cxx
  config_impl.cxx
  main-view_impl.cxx
  main-controller_impl.cxx
  project_impl.cxx
  project-factory_impl.cxx
  project-ui-factory_impl.cxx
  project-view_impl.cxx
  project-controller_impl.cxx
  wbs-view_impl.cxx
  wbs-controller_impl.cxx
  resources-view_impl.cxx
  resources-controller_impl.cxx
  gantt-view_impl.cxx
  gantt-controller_impl.cxx
  resource-usage-view_impl.cxx
  resource-usage-controller_impl.cxx

  util.cxx
  task.cxx
  wbs_impl.cxx
  wbs-gtk-tree-model.cxx
  )


target_include_directories(app
  PUBLIC ${GTKMM_INCLUDE_DIRS}
  )

target_link_libraries (app
  ${CMAKE_THREAD_LIBS_INIT}
  ${Boost_LIBRARIES}
  ${GTKMM_LIBRARIES}
  )

add_executable (thittam
  main.cxx
  interfaces.gresources.c
  )

target_link_libraries (thittam
  app
  )

install (TARGETS thittam DESTINATION bin)
