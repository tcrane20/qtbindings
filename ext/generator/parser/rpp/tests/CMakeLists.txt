set( EXECUTABLE_OUTPUT_PATH ${CMAKE_CURRENT_BINARY_DIR} )
include_directories( ${CMAKE_SOURCE_DIR}/languages/cpp/parser ${CMAKE_CURRENT_SOURCE_DIR}/..  )


########### next target ###############

set(pp_SRCS
    main.cpp
)

kde4_add_executable(pp TEST ${pp_SRCS})
target_link_libraries(pp ${KDE4_KDECORE_LIBS} kdev4cpprpp)

if (WIN32)
	# Realign the stack, for compatibility with an older ABI.
	set_target_properties (pp PROPERTIES COMPILE_FLAGS -mstackrealign)
endif (WIN32)
