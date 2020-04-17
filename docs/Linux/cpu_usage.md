# CPU使用相关

## CPU使用率限制

### cpulimit

来官方的介绍：

cpulimit is a simple program that attempts to limit the cpu usage of a process (expressed in percentage, not in cpu time). This is useful to control batch jobs, when you don't want them to eat too much cpu. It does not act on the nice value or other scheduling priority stuff, but on the real cpu usage. Also, it is able to adapt itself to the overall system load, dynamically and quickly.

该程序控制的是CPU的使用率

#### 下载
官方地址下载安装包

<http://cpulimit.sourceforge.net/>

或

    svn checkout https://cpulimit.svn.sourceforge.net/svnroot/cpulimit/trunkcpulimit 

#### 部署
    cd $cpulimit_home
    make 
    # 转移到/usr/bin文件夹
    cp ./cpulimit /usr/bin

#### 使用方法
>  Usage: cpulimit TARGET [OPTIONS...]

>  TARGET must be exactly one of these:

>&emsp;     -p, --pid=N        pid of the process (implies -z)

>&emsp;     -e, --exe=FILE     name of the executable program file or absolute path name

> OPTIONS

>&emsp;  -l, --limit=N      percentage of cpu allowed from 0 to 100 (required)

>&emsp;  -v, --verbose      show control statistics

>&emsp;  -z, --lazy         exit if there is no suitable target process, or if it dies

>&emsp;  -h, --help         display this help and exit

例如限制端口号为2816的程序使用CPU 55%：

    sudo cpulimit -p 2816 -l 55

使用sudo权限可以更好的工作

需要注意的是，-e要使用可执行文件，然后如果电脑有多个CPU的话可能不太适用，这个会将限制控制在100%以内，但是多个CPU的话可以超过100%，或许可以参考对每个线程或每个CPU上的使用进行分别的限制。

### 其他方法
暂时可以参考文献

<https://blog.csdn.net/fengmm521/article/details/78446439>

## CPU使用情况查询

    # 查询全部用户使用情况
    top
    # 之后在按下1就可以看到各个CPU的使用情况，或直接使用命令
    top -d 1
    
    
    # 查询某个用户
    top | grep $user_name
