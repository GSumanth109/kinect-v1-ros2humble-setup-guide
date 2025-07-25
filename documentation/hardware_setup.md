# Kinect v1 USB Wiring & Setup for ROS 2 Humble (Ubuntu 22.04)

This tutorial explains how to wire and connect an **Xbox 360 Kinect (v1)** sensor for use with **ROS 2 Humble** on **Ubuntu 22.04**. It's ideal for students and developers building SLAM or 3D mapping projects from scratch, especially when official adapters are unavailable or in my case, expensive.

---

## ⚠️ Warning

> 🔥 Incorrect wiring can permanently damage your Kinect. Double-check your connections and **never reverse power or data lines**. Always follow tested guides or diagrams.

---

## 🔧 Hardware Used

- **Kinect Sensor**: Xbox 360 Kinect (v1)
- **Cable**: Custom USB 2.0 cable (4-wire: VCC, GND, D+, D-)
- **Adapter**: 12V 2.5A power supply (recommended) (I found an old WiFi router adapter with the same specifications and it worked)
- **Optional Extension**: Short **Ethernet cable** to act as a makeshift modular adapter
- **OS & ROS**: Ubuntu 22.04 + ROS 2 Humble

---

## 🛠️ Wiring Guide

I followed this detailed [Instructables tutorial](https://www.instructables.com/Wiring-an-Xbox-Kinect-for-USB/) for the Kinect USB conversion.

> **Important Notes**:
> - Keep total wire length **under 2.5 meters** (USB 2.0 limitation).
> - Retain **at least one ferrite core** at the end of the cable to reduce data packet loss.
> - Use a **shielded Ethernet cable** if extending the connection — it reduces electrical noise better than normal wires.
> - Never blindly match colors; test and verify each pin manually with a multimeter if unsure.
> - If you reverse VCC and GND, you **can fry** the Kinect like I did on my first try.

I included a wiring diagram that I found on reddit in the same directory as this document. The wiring diagram works and I used the same diagram to build my setup.
I also included an image of my setup for reference if needed in the same directory.
