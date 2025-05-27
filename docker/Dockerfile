# Dockerfile.ros2-jazzy-gui
FROM ros:jazzy

# Install dependencies for ROS 2 packages and GUI tools
RUN apt-get update && apt-get install -y \
    ros-jazzy-rviz2 \
    ros-jazzy-rqt \
    ros-jazzy-rqt-common-plugins \
    x11-apps \
    python3-colcon-common-extensions \
    python3-rosdep \
    python3-rosinstall-generator \
    python3-vcstool \
    && rm -rf /var/lib/apt/lists/*

# Source ROS 2 setup
SHELL ["/bin/bash", "-c"]
RUN echo "source /opt/ros/jazzy/setup.bash" >> ~/.bashrc
