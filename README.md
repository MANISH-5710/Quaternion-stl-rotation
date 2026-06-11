# 3D Aircraft Quaternion Rotation Animator

An interactive 3D visualization tool that animates an aircraft 3D mesh (STL format) through a sequential **Yaw $\rightarrow$ Pitch $\rightarrow$ Roll** maneuver. 

The project uses quaternions for Spherical Linear Interpolation (**SLERP**) to ensure perfectly smooth transitions without gimbal lock. It features a live Heads-Up Display (HUD) showing real-time quaternion tracking data alongside body-fixed (local) and global reference coordinate systems.

## Features

* **Dual Rendering Engines:** Includes a hardware-accelerated **OpenGL window** for silky-smooth interactive live view, alongside a flexible **matplotlib 3D backend** for export.
* **Quaternion SLERP Tracking:** Computes intermediate rotations smoothly across discrete orientation milestones using the `pyquaternion` library.
* **Dynamic HUD Panel:** Displays instantaneous quaternion components ($w, x, y, z$), magnitude ($|q|$), sequence progress percentage, and target rotation thresholds.
* **Automatic Coordinate Realignment:** Centers external STL meshes precisely at their computed Center of Mass (COM) to guarantee stable in-place rotational spins.
* **Smart Mesh Optimization:** Optionally applies quadratic decimation to reduce polygon counts on ultra-high-resolution files when processing off-screen media.

---

## Installation

1. Ensure your Python virtual environment is activated.
2. Install the required external dependencies running the command below:

```bash
pip install numpy trimesh pyglet pyquaternion matplotlib pillow



The script intelligently adapts based on the arguments supplied via your command line interface.

1. Interactive Live Mode (Default Engine)
Launches a hardware-accelerated OpenGL visualization window using pyglet. This supports real-time mouse inputs to orbit, track, or scroll-zoom fluidly around the spinning mesh.

Bash
python "Quaternion rotator.py"
2. Export Video or GIF File Mode
Renders the complete sequential orientation sequence off-screen and writes it down to a media file using matplotlib's rendering system.

Bash
# Save as a standard MP4 video file
python "Quaternion rotator.py" --save flight_maneuver.mp4

# Save as an animated GIF running at customized frame constraints
python "Quaternion rotator.py" --save flight_maneuver.gif --frames 180 --fps 30
3. Matplotlib Evaluation Mode
Launches the legacy interactive matplotlib 3D plotting grid workspace. Useful for headless setups, custom view angle adjustments, or basic frame-by-frame debug tracking.

Bash
python "Quaternion rotator.py" --mpl

