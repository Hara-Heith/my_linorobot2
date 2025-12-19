#### Visualize the newly created URDF:
ros2 launch linorobot2_description description.launch.py rviz:=true

#### Using Gazebo:
ros2 launch linorobot2_gazebo gazebo.launch.py

ros2 launch linorobot2_gazebo gazebo.launch.py world:=empty.world

ros2 launch linorobot2_gazebo gazebo.launch.py rviz:=true world:=empty.world

ros2 run tf2_tools view_frames

#### Keyboard Teleop:
ros2 run teleop_twist_keyboard teleop_twist_keyboard

------------------------------------------------------------------------------

colcon build
source ~/.bashrc
ros2 launch linorobot2_gazebo gazebo.launch.py world:=empty.world