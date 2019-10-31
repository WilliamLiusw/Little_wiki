# rospy

## 初始化、节点挂起和关闭

    rospy.init_node (name,anonymous=False,log_level=rospy.INFO，disable_signals=False) 
    # 初始化节点
    # anoymous=True 通过在你名字的后边添加一个随机数，来保证你的节点独一无二。
    rospy.spin() # 挂起节点，需要指出的是，执行该语句后将不能再执行其他后面的语句
    
    # Ctrl+c 等可以关闭节点
    rospy.on_shutdown(h) # 关闭节点后执行函数h，但如果是publish则不能保证真的能发出去
    
## 接收消息和发布消息
### 接收消息
    rospy.Subscriber('topic_name',msg_type,callback_function)
    def callback_function(msg)

### 发布消息
    pub = rospy.Publisher(‘topic_name’,msg_type,queue_size=10)
    pub.publish(msg)
queue_size：

* queue_size: None（不建议） 这将设置为阻塞式同步收发模式！
* queue_size: 0（不建议）这将设置为无限缓冲区模式，很危险！
* queue_size:1,2,3；对于只关心最新数据的sensor消息，可以设为1； 对于系统负载不高，能及时处理的消息，可以设为1，2，3.
* queue_size: 10 or more ；一般情况下，设为10 。queue_size太大了会导致数据延迟不同步。

## 时间相关
* time和duration是rospy中两个重要的时间概念

&emsp;&emsp;&emsp; time指时刻，类型是rospy.Time。

&emsp;&emsp;&emsp; duration指时段，类型是rospy.Duration

&emsp;&emsp;&emsp; 两者单位一样，直接print则是纳秒。数值形式一样：int32 secs、int32 nsecs

* timer：rospy的定时器

        rospy.Timer(period, callback, oneshot=False)
        # period，调用回调函数的时间间隔，如rospy.Duration(0.1)即为10分之1秒。
        # callback，定义回调函数，会传递TimerEvent实例
        # oneshot，定时器，是否执行多次。false即一直执行
    
        def callback(TimerEvent)
        # TimerEvent的内部属性包括：
        # current_expected: 理想值，这次callback的被调用时刻。
        # current_real: 现实值，这次callback的被调用时刻。
        # last_expected: 上次的理想值。
        # last_real: 上次的现实值。
        # last_duration: 上次callback的持续时段
    
## 参数服务器
### Getting parameters
    global_name = rospy.get_param(“/global_name”)
    relative_name = rospy.get_param(“relative_name”)
    private_param = rospy.get_param(‘~private_name’)
    default_param = rospy.get_param(‘default_param’,‘default_value’)
    
    fetch a group (dictionary) of parameters
    gains = rospy.get_param(‘gains’)
    p, i, d = gains[‘P’], gains[‘I’],gains[‘D’]

### Setting parameters
    rospy.set_param(‘a_string’, ‘baz’)
    rospy.set_param(‘~private_int’, 2) 
    rospy.set_param(‘list_of_floats’, [1., 2., 3., 4.])
    rospy.set_param(‘bool_True’, True)
    rospy.set_param(‘gains’, {‘p’: 1, ‘i’: 2,‘d’: 3})

### Deleting parameters
    rospy.delete_param(param_name)

### Parameter existence
    rospy.has_param(param_name)

执行get_param()和delete_param()前，最好检查一下参数名是否存在。否则会引发KeyError异常。

## Exceptions
* ROSException：ROS相关异常的基类。
* ROSSerializationException：ROS消息串行化异常！
* ROSInitException： ROS初始化异常！
* ROSInterruptException：ROS中断异常！
* ROSInternalException：ROS内部异常！
* ServiceException：Service通信异常！
