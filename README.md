# zed-ros-wrapper
Ros wrapper for the ZED Stereo Camera SDK

**This sample is designed to work with the ZED stereo camera only and requires the ZED SDK. For more information: https://www.stereolabs.com**

**This wrapper also requires the PCL library**

This sample is a wrapper for the ZED library in order to use the ZED Camera with ROS. It can provide the camera images, the depth map, and a 3D point cloud
Published topics:

   - /camera/point_cloud/cloud
   - /camera/depth/camera_info
   - /camera/depth/image_rect_color
   - /camera/left/camera_info
   - /camera/left/image_rect_color
   - /camera/rgb/camera_info
   - /camera/rgb/image_rect_color

A set of parameters can be specified in the launch file provided in the launch directory.

   - zed.launch

The zed_ros_wrapper is a catkin package made to run on ROS Indigo, and depends
on the following ROS packages:

   - roscpp
   - rosconsole
   - sensor_msgs
   - opencv2
   - cv_bridge
   - image_transport

## Build the program

Place the package folder "zed_wrapper" in your catkin workspace source folder "~/catkin_ws/src"

Open a terminal :

    $ cd ~/catkin_ws
    $ catkin_make
    $ source ./devel/setup.bash


## Run the program

   Open a terminal to launch the wrapper:

   	$ roslaunch zed_wrapper zed.launch

   Open an other terminal to display images:

   	$ rosrun image_view image_view image:=/camera/rgb/image_rect_color

   If you want to see the point cloud, launch rviz, select zed_optical_frame in Displays->Global Options->Fixed Frame->zed_optical_frame.
   Then click on 'add' (bottom left), select the 'By Topic' tab, select point_cloud->cloud->PointCloud2 and click 'OK'.
   
   	$ rosrun rviz rviz

   Note that rviz isn't very good at displaying a camera feed and a point cloud at the same time. You should use an other instance of rviz or the `rosrun` command.

## Launch file parameters

 Parameter              |           Description           |              Value                
------------------------|---------------------------------|---------------------------------  
 svo_file               | SVO filename                    | path to an SVO file               
 resolution             | ZED Camera resolution           | '0': HD2K                         
 _                      | _                               | '1': HD1080                       
 _                      | _                               | '2': HD720                        
 _                      | _                               | '3': VGA                          
 quality                | Disparity Map quality           | '1': PERFORMANCE                  
 _                      | _                               | '2': QUALITY                      
 sensing_mode           | Depth sensing mode              | '0': FULL                         
 _                      | _                               | '1': RAW                          
 frame_rate             | Rate at which images are published                          | int   
 rgb_topic              | Topic to which rgb==default==left images are published      | string
 rgb_cam_info_topic     | Topic to which rgb==default==left camera info are published | string
 rgb_frame_id           | ID specified in the rgb==default==left image message header | string
 left_topic             | Topic to which left images are published                    | string
 left_cam_info_topic    | Topic to which left camera info are published               | string
 left_frame_id          | ID specified in the left image message header               | string
 right_topic            | Topic to which right images are published                   | string
 right_cam_info_topic   | Topic to which right camera info are published              | string
 right_frame_id         | ID specified in the right image message header              | string
 depth_topic            | Topic to which depth map images are published               | string
 depth_cam_info_topic   | Topic to which depth camera info are published              | string
 depth_frame_id         | ID specified in the depth image message header              | string
 point_cloud_topic      | Topic to which point clouds are published                   | string
 cloud_frame_id         | ID specified in the point cloud message header              | string












