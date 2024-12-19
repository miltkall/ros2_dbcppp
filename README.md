# ros2_dbcppp CURRENTLY WORK IN PROGRESS

ROS 2 wrapper for the dbcppp library, which provides DBC file parsing capabilities for CAN bus configurations.

## Overview

This package wraps the [dbcppp](https://github.com/xR3b0rn/dbcppp) library for use in ROS 2 environments. It provides CMake integration and proper installation of the library in the ROS ecosystem.

## Dependencies

- ROS 2 (Humble or later recommended)
- Boost
- LibXml2 (optional, for KCD support)

## Installation

### From Source

```bash
# Create a ROS workspace
mkdir -p ~/ros2_ws/src
cd ~/ros2_ws/src

# Clone this repository
git clone --recursive https://github.com/your-org/ros2_dbcppp.git

# Install dependencies
sudo apt-get update
sudo apt-get install libboost-dev libxml2-dev

# Build the workspace
cd ~/ros2_ws
colcon build --packages-select ros2_dbcppp

# Source the workspace
source install/setup.bash
```

## Usage

To use this package in your ROS 2 project, add it as a dependency in your `package.xml`:

```xml
<depend>ros2_dbcppp</depend>
```

And in your `CMakeLists.txt`:

```cmake
find_package(ros2_dbcppp REQUIRED)
ament_target_dependencies(${PROJECT_NAME}
  ros2_dbcppp
)
```


