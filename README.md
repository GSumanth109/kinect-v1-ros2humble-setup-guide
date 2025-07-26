
# Kinect v1 with ROS 2 Humble + RTAB-Map

This project documents how to interface the Xbox Kinect v1 sensor with ROS 2 Humble on Ubuntu 22.04 for real-time 3D room mapping using RTAB-Map. It includes complete setup instructions for both hardware wiring and software configuration, along with sample outputs for reference.

The goal is to fill the gap in available resources for getting Kinect v1 working with ROS 2, especially for users looking to use it with RTAB-Map on a modern system. It took me some time to find out and hopefully it won't be the same for you.

---

## 🔧 What’s Included

- A **hardware setup guide** (`setup.md`) showing how to wire the Kinect to USB and power.
- A **software setup guide** (`software_setup.md`) for building the `kinect_ros2` driver and using it with RTAB-Map.
- A **results** folder with sample outputs from RViz and exported `.ply` point cloud files.

---

## 🙏 Credits and References

- 🔌 **Wiring Guide**: [Wiring an Xbox Kinect for USB (Instructables)](https://www.instructables.com/Wiring-an-Xbox-Kinect-for-USB/)
- 📦 **Kinect ROS 2 Package**: [matlabbe/kinect_ros2](https://github.com/matlabbe/kinect_ros2)
- ❓ **Discussion Forum**: [RTAB-Map GitHub Discussions #1124](https://github.com/introlab/rtabmap/discussions/1124)
- 🎥 **YouTube Proof**: [RTAB-Map Kinect Setup on ROS 2 (YouTube)](https://www.youtube.com/watch?v=MBq0YxG41O8)

Huge thanks to the **Tjaart Kotze** youtube channel for showcasing his resources on his videos. His discussion forum that I linked above has detailed instructions to install it without many issues. 
---

## 📌 Note

If you're facing issues or trying to expand this further (e.g., adding environmental change detection or trajectory prediction), check the `Future Work` section in the `README` or browse the GitHub Discussions listed above. Contributions are welcome! 

