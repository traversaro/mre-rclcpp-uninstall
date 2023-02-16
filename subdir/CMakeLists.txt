option(USES_RCLCPP "Run find_package(rclcpp)" ON)

if(USES_RCLCPP)
  find_package(rclcpp)
endif()
