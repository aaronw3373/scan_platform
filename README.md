# scan_platform
ros related code to control a platform for 3D scanning of objects

 # Run Test:
 - roscore
 - sudo chmod a+rw /dev/ttyACM0 or USB0 whichever shows
 - rosrun rosserial_python serial_node.py _port:=/dev/ttyACM0 (or USB0)
 - rostopic pub --once /scan_increment std_msgs/Float64 "data: 180.0"


 # To Take Scan:
 - roscore
 - sudo chmod a+rw /dev/ttyACM0 or USB0 whichever shows
 - rosrun rosserial_python serial_node.py /dev/ttyACM0 (or USB0)
 - roslaunch src/scan_platform/ros_stepper_scan/stepper_scan.launch 
 - roslaunch kinect2_bridge kinect2_bridge.launch (may have to run off luc's see notes)
 - rosservice call /start_stepper_scan "model_name: 'put_name_of_object_here'"



Notes:
1. if error connecting to arduino when:
rosrun rosserial_python serial_node.py /dev/ttyACM0
resart computer

2. if rostopic list doesn't show all the kinect topics then
su luc
password: JinxAbbyMerry
roslaunch kinect2_bridge kinect2_bridge.launch

3. to view point cloud file 
pcl_viewer catkin_ws/devel/lib/ros_stepper_scan/<file-name>

