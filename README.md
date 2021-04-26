# turtlebot_control


开发一个独立的ROS功能包，借助turtlebot3 burger实现如下功能

- 节点一：
  - 订阅小车odom "/ugv1/odom" （仿真中才有，实际中使用vicon得到odom）
  - 订阅上层控制指令 【这个话题请使用自定义msg】  "/ugv1/control_cmd"
  - 发布小车底层控制指令  "/ugv1/cmd_vel"
  - 功能：
    - 上层控制指令若发来的是一个点，如（1,0，120），则小车移动到（1，0）这个点、并偏航角锁定为120度
    - 上层控制指令若发来的是线速度及角速度，则直接执行该速度
    - 请打印上层控制指令、小车odom等关键信息用于监控

- 节点二：
  - 发布上层控制指令   "/ugv1/control_cmd"
  - 功能：
    - 可以通过terminal交互，发送不同的上层控制指令



说明：

- C语言编写
- 使用ENU及FLU坐标系，即车头逆时针旋转时，偏航角为正
- 仿真中先启动 roslaunch prometheus_gazebo sitl_cxy_case2_1ugv.launch即可得到odom信息
