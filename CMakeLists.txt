cmake_minimum_required(VERSION 3.10)
project(bno055_vendor)

find_package(ament_cmake REQUIRED)

add_library(bno055 STATIC bno055.c)

target_include_directories(bno055 PUBLIC
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
  $<INSTALL_INTERFACE:include>
)

set_target_properties(bno055 PROPERTIES
  C_STANDARD 99
  C_STANDARD_REQUIRED ON
  POSITION_INDEPENDENT_CODE ON
)

install(TARGETS bno055 EXPORT bno055Targets)
install(FILES bno055.h DESTINATION include)

ament_export_targets(bno055Targets HAS_LIBRARY_TARGET)

ament_package()
