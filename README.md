# my_py_pkg

A small ROS 2 Python package (`ament_python` build type) demonstrating a
publisher/subscriber pair.

## Package overview

| Item | Value |
|------|-------|
| Package name | `my_py_pkg` |
| Build type | `ament_python` |
| Topic name | `/my_topic` |
| Message type | `std_msgs/msg/String` |
| Publisher executable | `pub` |
| Subscriber executable | `sub` |
| Launch file | `launch/pubsub.launch.py` |

## Nodes

### `my_py_pkg.my_py_node` (executable: `pub`)

A `MinimalPublisher` node that periodically publishes a `std_msgs::msg::String`
message on the topic `/my_topic` every 0.5 seconds. The message payload is
`Hello World: <n>`, where `n` is a monotonically increasing counter.

### `my_py_pkg.my_sub_node` (executable: `sub`)

A `MinimalSubscriber` node that subscribes to `/my_topic` and logs each
received message as `I heard: "<data>"`.

Both nodes are registered as console-script entry points in `setup.py`, so they
can be run with `ros2 run`:

```bash
ros2 run my_py_pkg pub
ros2 run my_py_pkg sub
```

## Launch file

`pubsub.launch.py` starts both nodes together in a single command:

```bash
ros2 launch my_py_pkg pubsub.launch.py
```

## Build and run

This package is part of a ROS 2 workspace (`~/ros2_ws`). ROS 2 Jazzy is required.

### Build

```bash
# 1. Source the ROS 2 installation
source /opt/ros/jazzy/setup.bash

# 2. Build the workspace (from ~/ros2_ws)
cd ~/ros2_ws
colcon build --packages-select my_py_pkg

# 3. Source the install space
source install/setup.bash
```

### Run

Run both nodes together:

```bash
ros2 launch my_py_pkg pubsub.launch.py
```

Or run each node individually:

```bash
ros2 run my_py_pkg pub
ros2 run my_py_pkg sub
```

## Repository

<https://github.com/NagarajaAcharya1/my_py_pkg>