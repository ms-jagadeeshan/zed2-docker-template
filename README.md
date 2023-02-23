# ZED2 Dockerfile Templates

## Building docker image locally

- ROS1 + Noetic
```
bash build-ros-desktop-image.sh
```

- ROS 2 + Noetic  
Edit [this](./build-ros-desktop-image.sh#L20) to 1 and run below command
```
bash build-ros-desktop-image.sh
```

- ROS 1 + jetson
```
bash build-ros-jetson-image.sh
```

## Already build image
https://hub.docker.com/repository/docker/jagamatrix/zed2-docker/general


- ROS 1 minimal + desktop(Recommeneded)
```bash
docker pull jagamatrix/zed2-docker:desktop-minimal
```

- ROS 1 + Neotic
```bash
docker pull jagamatrix/zed2-docker:desktop
```
- ROS 1 + jetson
```bash
docker pull jagamatrix/zed2-docker:jetson
```

## Usage

### Creating

- Nvidia + network(Recommended)
```bash
# xhost +si:localuser:root
docker create -it \
    --gpus all \
    -e NVIDIA_DRIVER_CAPABILITIES=all \
    --runtime nvidia \
    --privileged \
    --network=host \
    -v /dev:/dev \
    --name zed2-docker-minimal  \
    jagamatrix/zed2-docker:desktop-minimal
```

- Nvidia + network + display 
```bash
xhost +si:localuser:root
docker create -it \
    --gpus all \
    -e NVIDIA_DRIVER_CAPABILITIES=all \
    --runtime nvidia \
    --privileged \
    --network=host \
    -v /dev:/dev \
    -e DISPLAY \
    -v /tmp/.X11-unix:/tmp/.X11-unix \
    --name zed2-docker \
    jagamatrix/zed2-docker:desktop
```

### Starting and running

- Start the docker and run
```bash
# Starting docker
docker start zed2-docker-minimal

docker exec -it zed2-docker-minimal /ros_entrypoint.sh roslaunch zed_wrapper zed2i.launch
```

- Host machine
```
rviz -d zed2i.rviz
```

