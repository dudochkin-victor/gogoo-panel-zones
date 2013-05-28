INCLUDE_DIRECTORIES(
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${MPL_INCLUDE_DIRS}
    ${WNCK_INCLUDE_DIRS}
    ${CLUTTER_GTK_INCLUDE_DIRS}
    ${GCONF_INCLUDE_DIRS}
    )

SET (PROGRAMS gogoo-panel-zones)

ADD_DEFINITIONS(-DLOCALEDIR="${LOCALEDIR}")
ADD_DEFINITIONS(-DMX_CACHE="${DATADIR}/mx.cache")
ADD_DEFINITIONS(-DTHEMEDIR="${PKG_DATADIR}/${PROGRAMS}/theme")
ADD_DEFINITIONS(-DGETTEXT_PACKAGE="${GETTEXT_PACKAGE}")
ADD_DEFINITIONS(-DDATADIR="${PKG_DATADIR}/${PROGRAMS}")

SET(PROGRAM_SRCS
     penge-magic-texture.c 
     penge-magic-texture.h 
     sw-overview.c 
     sw-overview.h 
     sw-window.c 
     sw-window.h 
     sw-zone.c 
     sw-zone.h 
     main.c
    )

SET(PROGRAM_HEADERS
    )

ADD_EXECUTABLE(${PROGRAMS} ${PROGRAM_SRCS} ${PROGRAM_HEADERS})

   
TARGET_LINK_LIBRARIES(${PROGRAMS}
    ${WNCK_LIBRARIES}
    ${MPL_LIBRARIES}
    ${CLUTTER_GTK_LIBRARIES}
    ${GCONF_LIBRARIES}
    )

INSTALL(TARGETS ${PROGRAMS} RUNTIME DESTINATION ${PKG_LIBEXECDIR})

########### Add .service target ###############
CONFIGURE_FILE(
  "${CMAKE_CURRENT_SOURCE_DIR}/com.meego.UX.Shell.Panels.zones.service.in"
  "${CMAKE_CURRENT_BINARY_DIR}/com.meego.UX.Shell.Panels.zones.service"
  IMMEDIATE @ONLY)
INSTALL(FILES ${CMAKE_CURRENT_BINARY_DIR}/com.meego.UX.Shell.Panels.zones.service DESTINATION share/dbus-1/services)


