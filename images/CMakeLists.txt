# Set SVG executable
SET(SVG_COMPILE "inkscape")

# Get a list of svg files
FILE(GLOB_RECURSE SVG_FILES "*.svg")

FOREACH(file ${SVG_FILES})
  GET_FILENAME_COMPONENT(basename "${file}" NAME_WE)

  # Command to run svg
  IF(SVG_COMPILE)
    IF(NOT EXISTS ${CMAKE_CURRENT_BINARY_DIR}/${basename}.pdf)
      EXECUTE_PROCESS(
	COMMAND ${SVG_COMPILE}
	${CMAKE_CURRENT_SOURCE_DIR}/${basename}.svg
	-A ${CMAKE_CURRENT_BINARY_DIR}/${basename}.pdf
	)
    ENDIF()
  ENDIF(SVG_COMPILE)

  # Make a list of all svg files (for ADD_LATEX_DOCUMENT depend)
  SET(
    ALL_SVG_FILES ${ALL_SVG_FILES}
    ${CMAKE_CURRENT_BINARY_DIR}/${basename}.pdf
    PARENT_SCOPE
    )
ENDFOREACH(file)
