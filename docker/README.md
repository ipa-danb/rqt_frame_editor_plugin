xhost +local:docker

docker compose up --build

containers --> right click on ros2-jazzy-gui:latest --> attach shell

cd workspace
colcon build --symlink-install

source install/setup.sh && ros2 launch frame_editor frame_editor_launch.py