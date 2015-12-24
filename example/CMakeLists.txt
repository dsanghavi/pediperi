cmake_minimum_required (VERSION 2.6)

link_libraries(apriltags)

add_executable(apriltags_core apriltags_core.cpp Serial.cpp)
pods_install_executables(apriltags_core)

add_executable(imu imu.cpp Serial.cpp)
pods_install_executables(imu)
