This repository contains the simulation of the AgiBot G2 robot

# Setup Guide

- Clone this repository

- Get the assets necessary to run the simulations (must be in /home/<user>/)
```bash
  git clone https://huggingface.co/datasets/agibot-world/GenieSimAssets 
```
- Inside the container:
```
geniesim status                         
geniesim doctor                          
geniesim bootstrap                       
```

# Opening Simulator

- Open the simulator with a created scene
```
geniesim ros build dev
source devel/setup.bash

ros2 launch genie_sim_bringup app.launch.py \
  scene:=test_scene \
  launcher_config:=launcher_ovrtx_isaac_physx \
  headless:=false
```

## Other scenes available
| Scene | Robot | What it showcases |
|---|---|---|
| `scene_pnp_g2_op` | Genie G2 + **omnipicker** | Pick-and-place workflow |
| `scene_wbc_g2_sp` | Genie G2 + **swiftpicker** | Whole-body control workflow |

## Opening simulator with MoveIt

- After opening one of the available scenes, in a 2nd terminal run:
```
ros2 launch genie_sim_moveit wbc.launch.py
```

## More information on MoveIt
- Controlling the Isaac Sim camera from MoveIt's RViz window:
  1. In RViz, click **Add** → **By display type** → `genie_sim_rviz_plugins/ViewCameraPosePublisher`.
     Keep the default topic `/genie_sim_engine/viewer/camera_pose`. Moving the RViz view now moves the Isaac Sim free camera.
  2. Click **Add** → **By topic** → `/genie_sim/free_camera_rgb/image_raw` → **Camera** to show the rendered Isaac Sim view inside RViz.
  3. **File** → **Save Config** to keep these displays. A working reference is the `ViewCameraPosePublisher` + `Camera` pair in
     [view_robot.rviz](source/geniesim_ros/src/ros_ws/src/genie_sim_bringup/rviz/view_robot.rviz).

Further information lives in [geniesim_ros/src/README.md](geniesim_ros/src/README.md)

# Original README
The upstream Genie Sim README (features, module overview, benchmark leaderboard, changelog) lives in [docs/README.md](docs/README.md).
