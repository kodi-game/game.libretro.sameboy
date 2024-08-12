cmake_minimum_required(VERSION 3.10)

# Set the project name
project(hexdump)

# Add a custom target that calls the Makefile
add_custom_target(build_hexdump
  COMMAND ${CMAKE_MAKE_PROGRAM} -f Makefile
  WORKING_DIRECTORY ${CMAKE_SOURCE_DIR}
  COMMENT "Building hexdump using Makefile"
)

# Add a dummy install step that does nothing
add_custom_target(install_hexdump
  COMMAND ${CMAKE_COMMAND} -E echo "Skipping install step for hexdump"
)

# Override the default install target to avoid running it
set_target_properties(install_hexdump PROPERTIES EXCLUDE_FROM_ALL TRUE)

# Add an alias to build the hexdump by default when you build the project
add_custom_target(all_hexdump DEPENDS build_hexdump)
