ADD_SUBDIRECTORY(theme)

########### Add .desktop target ###############
CONFIGURE_FILE(
  "${CMAKE_CURRENT_SOURCE_DIR}/gogoo-panel-zones.desktop.in"
  "${CMAKE_CURRENT_BINARY_DIR}/gogoo-panel-zones.desktop"
  IMMEDIATE @ONLY)
INSTALL(FILES ${CMAKE_CURRENT_BINARY_DIR}/gogoo-panel-zones.desktop DESTINATION ${DATA_DIR}/panels)
INSTALL(FILES people.png DESTINATION ${PKG_DATADIR}/gogoo-panle-zones/theme)


