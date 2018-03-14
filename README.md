# rtsp_ros_driver

This ROS package contains a driver node that reads frames from an RTSP video stream (e.g., IP Camera) and publishes them out as [sensor_msgs/Image](http://docs.ros.org/api/sensor_msgs/html/msg/Image.html) ROS messages.


# Configuration

`rtsp_ros_driver` implements the ROS [camera_info_manager](http://wiki.ros.org/camera_info_manager_py) interface.
This means that the driver node can seamlessly handle camera calibration files. `rtsp_ros_driver` stores camera
calibration files in `$ROS_HOME/camera_info/` directory. Export the environment variable `$ROS_HOME` to point to
your `catkin_ws` dir.

```
 export ROS_HOME=<path_to_your_catkin_ws>
```


# Tutorial

You can launch the `rtsp_ros_driver` main node by running:

```
roslaunch rtsp_ros_driver rtsp_camera.launch <arguments>
```


# Launch files

## rtsp_camera.launch
Launches the main node of the package (i.e., `rtsp_driver_node`). Unless the `rtsp_driver_node` node, this launch file allows us to specify hostname, username, password, and other parameters about the camera separately. These parameters will be combined into a standard URL format and sent to the `rtsp_driver_node` node.

### Subscribed topics
None.

### Published topics
Identical to the `rtsp_driver_node` node (see below).

### Arguments

#### Mandatory arguments

_hostname_
  &nbsp;&nbsp;
  (`string`)
<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
    Hostname or IP of the RTSP camera.
    <br/> 

_username_
  &nbsp;&nbsp;
  (`string`)
<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
    Username for the RTSP camera.
    <br/>     

_password_
  &nbsp;&nbsp;
  (`string`)
<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
    Password for the RTSP camera.
    <br/>    

_stream_
  &nbsp;&nbsp;
  (`string`)
<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
    Name of the video stream published by the RTSP camera.
    <br/>    
    

#### Optional arguments

_camera\_name_
  &nbsp;&nbsp;
  (`string`, default: _rtsp\_camera_)
<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
    Namespace of the camera.
    <br/>

_camera\_frame_
  &nbsp;&nbsp;
  (`string`, default: _rtsp\_camera\_link_)
<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
    Name of the camera reference frame.
    <br/>

_image\_raw\_topic_
  &nbsp;&nbsp;
  (`string`, default: _~image\_raw_)
<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
    Name of the output image topic.
    <br/> 

_camera\_info\_topic_
  &nbsp;&nbsp;
  (`string`, default: _~camera\_info_)
<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
    Name of the output camera info topic.
    <br/> 

_port_
  &nbsp;&nbsp;
  (`int`, default: _554_)
<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
    Port of the RTSP camera.
    <br/>

    

# Nodes

## rtsp_driver_node
Main node of the package, it is responsible for reading frames from the given RTSP video stream source and publishing them out as [sensor_msgs/Image](http://docs.ros.org/api/sensor_msgs/html/msg/Image.html) ROS messages.

### Subscribed topics
None.

### Published topics

_/<camera\_name>/<image\_raw\_topic>_
  &nbsp;&nbsp;
  ([sensor_msgs/Image](http://docs.ros.org/api/sensor_msgs/html/msg/Image.html))
<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
    Raw image stream from the camera.
    <br/>
    
_/<camera\_name>/<camera\_info\_topic>_
  &nbsp;&nbsp;
  ([sensor_msgs/CameraInfo](http://docs.ros.org/api/sensor_msgs/html/msg/CameraInfo.html))
<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
    Camera metadata.
    <br/>

### Parameters

#### Mandatory parameters

_rtsp\_resource_
  &nbsp;&nbsp;
  (`string`)
<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
    RTSP URL to the camera string.
    <br/>


#### Optional parameters

_camera\_name_
  &nbsp;&nbsp;
  (`string`, default: _rtsp\_camera_)
<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
    Namespace of the camera.
    <br/>

_camera\_frame_
  &nbsp;&nbsp;
  (`string`, default: _rtsp\_camera\_link_)
<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
    Name of the camera reference frame.
    <br/>

_image\_raw\_topic_
  &nbsp;&nbsp;
  (`string`, default: _~image\_raw_)
<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
    Name of the output image topic.
    <br/> 

_camera\_info\_topic_
  &nbsp;&nbsp;
  (`string`, default: _~camera\_info_)
<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
    Name of the output camera info topic.
    <br/> 
