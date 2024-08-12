cmake_minimum_required(VERSION 3.10)

# Set the project name
project(hexdump)

# Add a custom target that calls the Makefile
add_custom_target(build_hexdump
  COMMAND ${CMAKE_MAKE_PROGRAM} -f Makefile
  WORKING_DIRECTORY ${CMAKE_SOURCE_DIR}
  COMMENT "Building hexdump using Makefile"
)

# Make the default build target depend on the build_hexdump target
add_custom_target(all
 DEPENDS build_hexdump
)
