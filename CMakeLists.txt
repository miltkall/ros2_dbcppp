cmake_minimum_required(VERSION 3.12)

project("ros2_dbcppp" VERSION 3.8.0)


# Configuration
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 17)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# Configure dbcppp options
option(build_tools OFF)
option(build_tests OFF)
option(build_examples OFF)
option(build_kcd OFF)

# Dependencies
find_package(ament_cmake REQUIRED)
find_package(Boost REQUIRED)
if(build_kcd)
  find_package(LibXml2 REQUIRED)
endif()

# Add subdirectories
add_subdirectory(dbcppp)

# Exports 
# To use the in other ROS packages
ament_export_include_directories(include)
ament_export_libraries(dbcppp)
ament_export_dependencies(Boost)

if(build_kcd)
  ament_export_libraries(libxmlmm)
  ament_export_dependencies(LibXml2)
endif()

ament_package()