# Vision-Based Target Tracking Turret

A two-axis pan/tilt turret that uses real-time computer vision to detect and track a person, then aims a servo-controlled platform at them using closed-loop PID control. Built on an ESP32 microcontroller with an OpenCV-based detection and control pipeline running on a host laptop.

## Overview

A USB camera feeds live video to a Python script running Haar cascade face detection. The detected target's pixel offset from frame center is calculated each frame and passed through independent PID controllers for the pan and tilt axes. The resulting correction values are streamed over USB serial to an ESP32, which drives two MG996R servos to keep the target centered in frame in real time.

A laser sight, boresighted to the platform, and a servo-actuated trigger mechanism (currently mounted on a Nerf SharpFire) provide a physical demo payload. A manual controller override mode allows direct pan/tilt/fire control, with input arbitration between autonomous tracking and manual control.

## Features
- Real-time face detection and tracking (OpenCV, Haar cascade)
- Independent PID control loops for pan and tilt axes
- Python-to-ESP32 serial command protocol
- Servo-driven pan/tilt platform (MG996R x2)
- Laser sight for visual aim confirmation, boresighted to barrel
- Servo-actuated trigger mechanism
- Manual override via game controller input, with mode arbitration between autonomous and manual control

## Hardware
- ESP32-WROOM-32 dev board
- 2x MG996R servo (pan, tilt)
- 1x SG90 servo (trigger)
- USB camera module (720p)
- 650nm laser diode module
- Nerf SharpFire (payload)

## Status
In progress. Pan-axis tracking loop (camera -> PID -> serial -> servo) confirmed working. Tilt axis, physical mounting, laser boresighting, and controller override pending.
