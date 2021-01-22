# relay_field_python3

partial copy of [ros/ros_comm](https://github.com/ros/ros_comm) with improvements

## Prerequisites

- Ubuntu 20.04
- ROS Noetic

## Usage

```sh
wget https://raw.githubusercontent.com/kenji-miyake/relay_field_python3/main/relay_field
python3 relay_field {input_topic_name} {output_topic_name} {topic_type} {message_expression}
```

## Examples

```sh
python3 relay_field /pose_stamped /tf tf2_msgs/TFMessage "
transforms:
  - header:
      seq: 0
      stamp: m.header.stamp
      frame_id: 'map'
    child_frame_id: 'pose'
    transform:
      translation:
        x: m.pose.position.x
        y: m.pose.position.y
        z: m.pose.position.z
      rotation:
        x: m.pose.orientation.x
        y: m.pose.orientation.y
        z: m.pose.orientation.z
        w: m.pose.orientation.w"
```

```sh
python3 relay_field /pose /pose_stamped geometry_msgs/PoseStamped "
header: auto
pose: m"
```

```sh
python3 relay_field /pose_stamped /pose geometry_msgs/Pose "
position: m.pose.position
orientation: m.pose.orientation"
```
