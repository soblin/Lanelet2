cmake_minimum_required(VERSION 3.5.1)
project(lanelet2_io)

find_package(ament_cmake_auto REQUIRED)
ament_auto_find_build_dependencies()
# Find the non-obvious packages manually
find_package(Boost REQUIRED)
find_package(Eigen3 REQUIRED)

find_library(PUGIXML_LIBRARIES
  NAMES pugixml
)
find_path(PUGIXML_INCLUDE_DIRS
  NAMES pugixml.hpp
  PATH_SUFFIXES pugixml
)
include_directories(
  ${PUGIXML_INCLUDE_DIRS}
)
file(GLOB_RECURSE PROJECT_SOURCE_FILES_SRC "src/*")

ament_auto_add_library(${PROJECT_NAME} SHARED
  ${PROJECT_SOURCE_FILES_SRC}
)
target_link_libraries(${PROJECT_NAME} ${PUGIXML_LIBRARIES})
target_include_directories(${PROJECT_NAME}
  SYSTEM PUBLIC
  ${BOOST_INCLUDE_DIRS}
  ${EIGEN3_INCLUDE_DIR}
)

ament_auto_package()
