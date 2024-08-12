cmake_minimum_required(VERSION 3.10)

# Set the project name
project(hexdump)

# Add a custom target that calls the Makefile to build the 'hexdump' binary
add_custom_target(build_hexdump ALL
  COMMAND ${CMAKE_MAKE_PROGRAM} CFLAGS="-Wno-error=clobbered" -f Makefile
  WORKING_DIRECTORY ${CMAKE_SOURCE_DIR}
  COMMENT "Building hexdump binary using Makefile"
)

# Install target to copy the binary to the specified directory
install(
  PROGRAMS ${CMAKE_SOURCE_DIR}/hexdump
  DESTINATION bin
)
