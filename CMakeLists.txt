cmake_minimum_required(VERSION 3.0.2)
project(occupancy_grid_map)
add_compile_options(-std=c++14)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  grid_map_core
  grid_map_ros
  grid_map_msgs
  nav_msgs
)

catkin_package(
  INCLUDE_DIRS 
    include
  LIBRARIES 
    occupancy_grid_map
  CATKIN_DEPENDS
    roscpp
    grid_map_core
    grid_map_ros
    grid_map_msgs
    nav_msgs
)

###########
## Build ##
###########
set(CMAKE_BUILD_TYPE Release)

include_directories(
  include
  ${catkin_INCLUDE_DIRS}
)

## Declare a C++ library
add_library(${PROJECT_NAME}
  src/OccupancyGridMap.cpp
  src/OccupancyGridMapHelper.cpp
  src/OccupancyGridMapRosConverter.cpp
)
target_link_libraries(${PROJECT_NAME}
  ${catkin_LIBRARIES}
)