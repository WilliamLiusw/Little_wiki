# python中的一些其他命令

## 输出多样化

    print(x, end="") # 指定输出尾部，默认为回车换行
    print(内容 \033[显示方式;字体色;背景色m 内容[\033[0m 内容) # 使用指定的样式进行输出

<img src="../pic/print_type.png" width = "300" alt="输出内容样式指令" align=center />

## 数字的无穷大

    ans = float('inf')

## 自定义Linux进程名

    import setproctitle
    setproctitle.setproctitle("your command name")

## 关于时间

### 程序运行时间计时

    import time
    time_start=time.time()
    time_end=time.time()
    print('time cost',time_end-time_start,'s')

### 获取电脑当前时间

    import time 
    print(time.strftime("%Y-%m-%d %H:%M:%S", time.localtime())) 
