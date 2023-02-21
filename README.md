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

- ROS 1 + Neotic
```
docker pull jagamatrix/zed2-docker:desktop
```
- ROS 1 + jetson
```
docker pull jagamatrix/zed2-docker:jetson
```

- ROS 1 minimal + desktop
```
docker pull jagamatrix/zed2-docker:desktop-minimal
```

