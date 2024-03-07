# realmove_yolo_ros2

This is a repository that uses yolo for object detection with ros2 humble.

## Docker

Build the Docker Image
```bash
cd_ws
docker build -t rm-yolo-dev -f .docker/Dockerfile .
```

Run the Container
```
docker run -it --rm --privileged --name <container_name> --mount type=bind,source=/ros/ros2_ws,target=/ros/ros2_ws -v /dev*:/dev* -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix <image_name> /bin/bash
```
or if you have the HRII env alias you can simply use:
```
docker_dev_run
```
Now you can build the ROS 2 package running the following command:

```bash
colcon build --packages-select realmove_yolo_ros2 --symlink-install
source install/setup.bash
```

## Run the Object Detection launch file
```bash
ros2 launch realmove_yolo_ros2 object_detection.launch.py
```
This creates an Object Detection node which is subscribed to the topic "/camera0/rgb", that performs the YOLO Object Detection on the received images and publishes them to a new topic. The subscriber nodes receives these images and displays them.
In order to see this, you need to launch the usb-cam. Check https://github.com/Real-Move/real-move-launcher.git for more information on how to do that. 

Otherwise you can edit the object_detection.launch.py file and uncomment the line: 
```
ld.add_action(publisher)
```
which will create a publisher that uses your camera directly (this is available for test purposes if you don't have access to the usb-cam)


## Useful things
If you get a QT Plugin error, just run the following command:
```bash
xhost +local:
```

If you want to visualise the nodes and topics, Install rqt
```bash
apt-get update
sudo apt install ros-humble-rqt* 
```
and run 
```
rqt_graph
```