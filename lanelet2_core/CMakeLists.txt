cmake_minimum_required(VERSION 3.5.1)
project(lanelet2_core)

find_package(ament_cmake_auto REQUIRED)
ament_auto_find_build_dependencies()
# Find the non-obvious packages manually
find_package(Boost REQUIRED)
find_package(Eigen3 REQUIRED)

file(GLOB_RECURSE PROJECT_SOURCE_FILES_SRC "src/*")

ament_auto_add_library(${PROJECT_NAME} SHARED
  ${PROJECT_SOURCE_FILES_SRC}
)
target_include_directories(${PROJECT_NAME}
  SYSTEM PUBLIC
  ${BOOST_INCLUDE_DIRS}
  ${EIGEN3_INCLUDE_DIR}
)
ament_target_dependencies(${PROJECT_NAME}
  Boost
  Eigen3
)

ament_auto_package(
  INSTALL_TO_SHARE
  res
)

# TODO(Mamoru Sobue)
# if (BUILD_TESTING)
# endif()
