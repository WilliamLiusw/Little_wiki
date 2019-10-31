# ROS命令集

## ros相关概念
* Nodes:节点,一个节点即为一个可执行文件，它可以通过ROS与其它节点进行通信。
一个节点其实只不过是ROS程序包中的一个可执行文件。ROS节点可以使用ROS客户库与其他节点通信。节点可以发布或接收一个话题。节点也可以提供或使用某种服务。

* Messages:消息，消息是一种ROS数据类型，用于订阅或发布到一个话题。
* Topics:话题,节点可以发布消息到话题，也可以订阅话题以接收消息。
* Master:节点管理器，ROS名称服务 (比如帮助节点找到彼此)。
* rosout: ROS中相当于stdout/stderr。
* roscore: 主机+ rosout + 参数服务器

## rosnode
用来显示当前运行的ROS节点信息。

* rosnode list指令列出活跃的节点；
* rosnode info命令返回的是关于一个特定节点的信息；

## rostopic
rostopic命令工具能让你获取有关ROS话题的信息。

* rostopic list                  print information about active topics
* rostopic echo [topic]   print messages to screen
* rostopic hz  [topic]      display publishing rate of topic
* rostopic type [topic]    print topic type
* rostopic pub  [topic] [msg_type] [args]    publish data to topic
* rostopic bw                           display bandwidth used by topic

## rosparam
* rosparam set            设置参数
* rosparam get            获取参数
* rosparam load           从文件读取参数
* rosparam dump           向文件中写入参数
* rosparam delete         删除参数
* rosparam list           列出参数名

## rosmsg
rosmsg当前的情况并不明了

* rosmsg show(显示消息)
* users(显示使用指定消息的代码)
* package(列出指定功能包中的所有消息)
* rosnode package 列出带有消息的所有功能包

## rosservice
服务（services）是节点之间通讯的另一种方式。服务允许节点发送请求（request）并获得一个响应（response）

* rosservice list          输出可用服务的信息
* rosservice call [service] [args]        调用带参数的服务
* rosservice type [service]        输出服务类型
* rosservice find         依据类型寻找服务find services by service type
* rosservice uri          输出服务的ROSRPC uri

## 其他命令
* roscd log：命令切换到ROS储存日志文件的目录。
* rosls：包含于rosbash package中，作用是列出指定的package或stack中的文件及目录


## ros工具
rosrun [package_name] [node_name]

rosrun rqt_graph rqt_graph 查看节点连接图
