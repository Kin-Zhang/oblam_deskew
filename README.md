# OBLAM Assignment: Deskewing lidar scan with IMU propagated states
<!-- via Continuous-time Optimization -->

The course materials and instructions can be found at [KTH Canvas](https://canvas.kth.se/courses/40649).

Please download the data [here](https://kth-my.sharepoint.com/:f:/g/personal/tmng_ug_kth_se/Em6tmNkGrJhHubL2o8PJ6gcB_iiLQJEIXDyOquTdF0o6jQ?e=JKDW3X)

Declare the path to the data in the launch file run_deskew.launch.

# Installation

## Dependencies

The software was developed on the following dependancies, Test System: [Ubuntu 20.04](https://releases.ubuntu.com/20.04/), [ROS Noetic full-desktop](http://wiki.ros.org/noetic/Installation)

Printer logger (glog, gflag are also dependencies on Ceres)

```bash
# maybe need sudo if you are running it in your desktop
curl -sL https://raw.githubusercontent.com/Kin-Zhang/Kin-Zhang/main/Dockerfiles/installGlog_ownenv.sh | bash
```

Solver: [Ceres 2.1.0](http://ceres-solver.org/installation.html) (do checkout the branch 2.1.0 after git clone)

```bash
git clone https://ceres-solver.googlesource.com/ceres-solver
git fetch --all --tags
git checkout tags/2.1.0
mkdir build && cd build
cmake .. && make -j$(nproc)
sudo make install
```

robot-localization package:

```bash
sudo apt install ros-noetic-robot-localization
```

## Build
Please install all dependencies first. Afterwards, create a ros workspace, clone the package to the workspace, and build by `catkin build` or `catkin_make`, for e.g.:

```
mkdir oblam/src
cd oblam/src
git clone https://github.com/Kin-Zhang/oblam_deskew
cd ../..; catkin build
```

## Run

After finished the assignment part, run the launch

```bash
source devel/setup.zsh
roslaunch oblam_deskew run_deskew.launch
```

# Results
## Demo
Go to the function PropagateIMU() and DeskewByImuPropagation() and add the codes to complete the motion compensation of the pointclouds. If sucess you should see the deskewed pointcloud on the right.

<details>
  <summary>Demo effects here</summary>

<p align="center">
    <img src="docs/deskew.gif" alt="mcd ntu daytime 04" width="99%"/>
</p>

</details>

## Kin's results

https://user-images.githubusercontent.com/35365764/209573586-f32bf567-e3ca-4303-a1e1-e69be37def12.mp4

![image](https://user-images.githubusercontent.com/35365764/209573645-1be4e5bd-f238-4b38-a7ba-e060ee162d74.png)