# RVIZ on Steam Deck

The following package was tested in ROS noetic.

## Setup ##

```
sudo pacman-key --populate holo
```

The following are some linux dependencies required to successfully execute this package in your configuration:

- Install base-devel:
    ```
    sudo pacman -Sy base-devel
    ```
- Net tools:
    ```
    sudo pacman -Sy net-tools
    ```
- Miniconda:
    ```
    mkdir -p ~/miniconda3
    wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh
    bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
    rm -rf ~/miniconda3/miniconda.sh
    # Finally make sure conda is configured at .bashrc
    ```
- Mamba:
    ```
    conda install mamba -c conda-forge
    mamba create -n ros_env python=3.11
    mamba activate noetic_dev # use this line to activate the ros noetic environment
    ```
- ROS noetic desktop:
    ```
    mamba activate noetic_dev # remember use this line to activate the ros noetic environment
    mamba install ros-noetic-desktop
    mamba install ros-noetic-joy
    ```

Finally, create a catkin_ws folder (or similar folder for your ros workspace):
```
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws/src
git clone https://github.com/aldajo92/steam_deck_rviz.git # cloning this repository
cd ~/catkin_ws
catkin_make
```

Execute this package:
```
source ~/catkin_ws/devel/setup.bash
roslaunch rviz_steamdeck rviz_steam.launch
```

# References #
- https://github.com/ICE9-Robotics/ROS-for-Steam-Deck-OLED
- https://github.com/ctu-vras/steam-deck-ros-controller?tab=readme-ov-file
- https://robostack.github.io/GettingStarted.html
