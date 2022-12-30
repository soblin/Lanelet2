cmake_minimum_required(VERSION 3.5.1)
project(lanelet2_validation)

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

# Add executables in "tools"
# glob_folders(TOOL_DIRECTORIES "${CMAKE_CURRENT_SOURCE_DIR}/tools")
# if (TOOL_DIRECTORIES)
#     # Found subfolders, add executable for each subfolder
#     foreach(TOOL_DIR ${TOOL_DIRECTORIES})
#         mrt_add_executable(${TOOL_DIR} FOLDER "tools/${TOOL_DIR}")
#     endforeach()
# else()
#     # No subfolder found, add executable and python modules for tools folder
#     mrt_add_executable(${PROJECT_NAME} FOLDER "tools")
# endif()

ament_auto_package()
