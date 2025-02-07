## 1. List the nodes running in the two-drone static scenario.
- /av1broadcaster
- /av2broadcaster
- /plots_publisher_node
- /frames_publisher_node
- /rviz2_node
- /transform_listener_impl_55f0637ce9e0
- /transform_listener_impl_56875e802940

## 2. How could you run the two-drone static scenario without using the ros2 launch command? List the commands that you would have to execute (in separate terminals) to achieve the same result.
```
ros2 run tf2_ros static_transform_publisher 1 0 0 0 0 0 world av1
ros2 run tf2_ros static_transform_publisher 0 0 1 0 0 0 world av2
ros2 run two_drones_pkg frames_publisher_node
ros2 run two_drones_pkg plots_publisher_node
ros2 run rviz2 rviz2 -d $(find-pkg-share two_drones_pkg)/config/default.rviz
```
## 3. List the topics that each node publishes / subscribes to. What nodes are responsible for publishing the av1, av2, frames? Which topic causes rViz to plot the drone meshes?

av boradacasters publish to tf, transform_listeners listen to /tf
plots publisher publihses to /visuals frames_publisher_node

MarkerArray is the topic which plots dronemeshes

## 4 What changes if we omit static:=True? Why?
If static is not true none of the nodes aren't launched for the drone frames and the dronemeshes do not show on the screen. This is because of the ocnditiona in the launch file.