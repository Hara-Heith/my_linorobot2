#### REMEMBER to connect to Portable hotspot
cd ~/linorobot2_ws
cd ~/simulation_data

#### Using a real robot:
colcon build &&
source ~/.bashrc &&
ros2 launch linorobot2_description description.launch.py rviz:=true

ros2 launch linorobot2_bringup bringup.launch.py base_serial_port:=/dev/ttyUSB0 offset_x:=1.1 offset_y:=0.8 offset_yaw:=0.0 lidar_serial_port:=/dev/ttyUSB1 micro_ros_baudrate:=921600

ros2 run linorobot2_control simple_follower_motion_law_av_rw --ros-args -p offset_x:=1.1 -p offset_y:=0.8 -p offset_phi:=0.0

ros2 run linorobot2_control fbl_follower_motion_law_av_rw --ros-args -p offset_x:=1.1 -p offset_y:=0.8 -p offset_phi:=0.0

ros2 run linorobot2_control fbl_follower_motion_law_av_po_rw --ros-args -p offset_x:=1.1 -p offset_y:=0.8 -p offset_phi:=0.0

ros2 run linorobot2_control lyapunov_follower_motion_law_av_rw --ros-args -p offset_x:=1.1 -p offset_y:=0.8 -p offset_phi:=0.0

ros2 run linorobot2_control mpc_ltv_follower_motion_law_av_rw --ros-args -p offset_x:=1.1 -p offset_y:=0.8 -p offset_phi:=0.0

#### Using Gazebo:
colcon build &&
source ~/.bashrc &&
ros2 launch linorobot2_gazebo gazebo.launch.py paused:=true rviz:=true world:=worlds/empty.world spawn_x:=1.1 spawn_y:=0.8 spawn_yaw:=0.0

ros2 run linorobot2_control simple_follower --ros-args -p offset_x:=1.1 -p offset_y:=0.8 -p offset_phi:=0.0

ros2 run linorobot2_control simple_follower_motion_law_av --ros-args -p offset_x:=1.1 -p offset_y:=0.8 -p offset_phi:=0.0

ros2 run linorobot2_control fbl_follower --ros-args -p offset_x:=1.1 -p offset_y:=0.8 -p offset_phi:=0.0

ros2 run linorobot2_control fbl_follower_motion_law_av --ros-args -p offset_x:=1.1 -p offset_y:=0.8 -p offset_phi:=0.0

ros2 run linorobot2_control lyapunov_follower --ros-args -p offset_x:=1.1 -p offset_y:=0.8 -p offset_phi:=0.0

ros2 run linorobot2_control lyapunov_follower_motion_law_av --ros-args -p offset_x:=1.1 -p offset_y:=0.8 -p offset_phi:=0.0

ros2 run linorobot2_control mpc_ltv_follower --ros-args -p offset_x:=1.1 -p offset_y:=0.8 -p offset_phi:=0.0

ros2 run linorobot2_control mpc_ltv_follower_motion_law_av --ros-args -p offset_x:=1.1 -p offset_y:=0.8 -p offset_phi:=0.0

#### Reset pose
ros2 topic pub --once /set_pose geometry_msgs/msg/Pose2D "{x: 0.0, y: 0.0, theta: 0.0}" &&
ros2 topic pub --once /set_pose geometry_msgs/msg/PoseWithCovarianceStamped "{header: {stamp: {sec: 0, nanosec: 0}, frame_id: 'odom'}, pose: {pose: {position: {x: 0.0, y: 0.0, z: 0.0}, orientation: {x: 0.0, y: 0.0, z: 0.0, w: 1.0}}}}"