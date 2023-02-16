option(USES_RCLCPP "Run find_package(rclcpp)" ON)

if(USES_RCLCPP)
  find_package(ament_cmake_core)
endif()
