cmake_minimum_required(VERSION 3.5)
project(shipcon_msgs)

# Default to C99
if(NOT CMAKE_C_STANDARD)
  set(CMAKE_C_STANDARD 99)
endif()

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package( ament_cmake REQUIRED )
find_package( rosidl_default_generators REQUIRED )
find_package( std_msgs )
find_package( geometry_msgs )


# Message Generation
set(msg_files
 "msg/device/common/SignalStatus.msg"
 "msg/device/motor/MotorCommand.msg"
 "msg/device/motor/MotorHealth.msg"
 "msg/device/motor/MotorInfo.msg"
 "msg/device/propeller/PropellerCommand.msg"
 "msg/device/propeller/PropellerHealth.msg"
 "msg/device/propeller/PropellerInfo.msg"
 "msg/device/rudder/RudderCommand.msg"
 "msg/device/rudder/RudderHealth.msg"
 "msg/device/rudder/RudderInfo.msg"
 "msg/device/gnss/GnssClock.msg"
 "msg/device/gnss/GnssHeading.msg"
 "msg/device/gnss/GnssPosition.msg"
 "msg/device/gyro/GyroInfo.msg"
 "msg/device/power/BatteryInfo.msg"
 "msg/device/power/PowerInfo.msg"
 "msg/device/rc_control/JoyInfo.msg"
 "msg/device/rc_control/ToggleInfo.msg"
 "msg/device/rc_control/RcInfo.msg"
 "msg/navigation/ControlMode.msg"
 "msg/navigation/NavigationInfo.msg"
 "msg/navigation/SpeedInfo.msg"
)

set(srv_files
  "srv/device/motor/GetMotorSpec.srv"
)

rosidl_generate_interfaces(${PROJECT_NAME}
  ${msg_files}
  ${srv_files}
  DEPENDENCIES std_msgs geometry_msgs
)
ament_package()