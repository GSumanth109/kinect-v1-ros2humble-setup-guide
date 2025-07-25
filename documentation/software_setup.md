# Kinect v1 ROS 2 Humble + RTAB-Map Software Setup

This document provides a step-by-step guide for integrating an Xbox Kinect v1 sensor with ROS 2 Humble and RTAB-Map on Ubuntu 22.04. The goal is to perform real-time 3D room mapping using the `kinect_ros2` driver and `rtabmap_ros`.

First, ensure you have the following installed: Ubuntu 22.04, ROS 2 Humble, RTAB-Map, `libfreenect-dev`, and `freenect`.

Install Freenect system dependencies:

```bash
sudo apt install libfreenect-dev freenect
```

Now create a new workspace and clone the Kinect driver:

```bash
mkdir -p ~/newKinect_ws/src
cd ~/newKinect_ws/src
git clone https://github.com/matlabbe/kinect_ros2
cd ..
rosdep install --from-paths src --ignore-src -r -y
colcon build --symlink-install
```

Note: `rosdep` may complain about unresolved freenect dependencies; these warnings can be ignored. Likewise, some build warnings like “stedder out” or stderr may appear but can be safely disregarded if the build completes successfully.

Open a new terminal and source your workspace:

```bash
source ~/newKinect_ws/install/setup.bash
ros2 run kinect_ros2 kinect_ros2_node
```

This starts the Kinect node, which begins publishing topics. In another terminal, list topics to verify:

```bash
ros2 topic list
```

At this point, you should see topics like `/rgb/image_raw`, `/depth/image_raw`, `/rgb/camera_info`, and `/depth/camera_info`.

You can visualize the RGB stream using:

```bash
ros2 run rqt_image_view rqt_image_view
```

And then selecting `/rgb/image_raw` from the dropdown menu.

Now launch RViz:

```bash
ros2 run rviz2 rviz2
```

You may notice that nothing is shown in RViz yet. This is normal—RTAB-Map needs to be launched next.

In another terminal, launch the Kinect-compatible RTAB-Map example:

```bash
ros2 launch rtabmap_examples kinect_xbox_360.launch.py
```

If RViz still shows no 3D map, it's likely due to mismatched topic names. To fix this, run the Kinect node again with remappings that align with what the RTAB-Map launch file expects:

```bash
ros2 run kinect_ros2 kinect_ros2_node --ros-args \
  --remap /rgb/image_raw:=/rtabmap/kinect/rgb/image_raw \
  --remap /rgb/camera_info:=/kinect/rgb/camera_info \
  --remap /depth/image_raw:=/kinect/depth_registered/image_raw
```

After this, the topics will align correctly with the RTAB-Map launch configuration. You should start seeing the point cloud and SLAM map update in RViz.

At this point, your setup is complete and working. This configuration allows full 3D room mapping using Kinect v1 and ROS 2. If you want to save your SLAM data, you can save the RTAB-Map database (`~/.ros/rtabmap.db`) before shutdown.
