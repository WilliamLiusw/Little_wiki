# 图像绘制
本节使用的package是Python的matplotlib.pyplot：

    import matplotlib.pyplot as plt

## 基础命令

    plt.figure() # 新建图像窗口
    plt.show() # 展示图像
    plt.savefig(path) # 存储图像
    
## 绘制折线图
### 简单图
#### 简单折线图

    plt.plot(x,y) #x为横轴，y为纵轴，两个数组应大小一致
    plt.show()

#### 简单直方图
    
    plt.bar(x,y) #x为横轴，y为纵轴，两个数组应大小一致
    plt.show()
    
### 标题、横纵轴设置
#### 标题文字

    plt.title(titlename)
    plt.xlabel(name)
    plt.ylabel(name)

#### 修改坐标轴刻度为文字

    scale_ls = range(7)
    index_ls = ['Mon','Tue','Wed','Thu','Fri','Sat','Sun']
    plt.xticks(scale_ls,index_ls)  # 可以设置坐标字
    # 同理，也有yticks()
    
#### 坐标轴限制

    pl.xlim(xmin, xmax)  # 限定横轴的范围
    pl.ylim(ymin, ymax)  # 限定纵轴的范围
    
### 图例
#### 和折线一起定义

    plt.plot(x1,y1,label=name1)
    plt.plot(x2,y2,label=name2)
    plt.legend()
其中legend函数可以接受一个一个loc关键字参数来设定图例的位置，可取值为数字或字符串：

<table>
    <tr>
        <th bgcolor=#000F00> 0 </th>  <th> 'best' </th>
        <th> 1 </th>  <th> 'upper right' </th>
        <th> 2 </th>  <th> 'upper left' </th>
    </tr>
    <tr>
        <th> 3 </th>  <th> 'lower left'</th>
        <th> 4 </th>  <th> 'lower right'</th>
        <th> 5 </th>  <th> 'right' </th>
    </tr>
    <tr>
        <th> 6 </th>  <th> 'center left' </th>
        <th> 7 </th>  <th> 'center right' </th>
        <th> 8</th>  <th> 'lower center' </th>
    </tr>
    <tr>
        <th> 9 </th>  <th> 'upper center' </th>
        <th> 10 </th>  <th> 'center' </th>
    </tr>
</table>

#### 和折线分开定义

    plt.plot(x1,y1)
    plt.plot(x2,y2)
    plt.legend(name1,name2)
    
### 折线样式
#### 颜色
plot方法的关键字参数color(或c)用来设置线的颜色，有四种设置方式：

* \#rrggbb
* (r, g, b) 或 (r, g, b, a)，其中 r g b a 取均为[0, 1]之间
* [0, 1]之间的浮点数的字符串形式，表示灰度值。0表示黑色，1表示白色
* 颜色名称或简写

b: blue|g: green|r: red|k: black
-|-|-|-
c: cyan|m: magenta|y: yellow|w: white

#### 线条样式
plot方法的关键字参数linestyle(或ls)用来设置线的样式。可取值为：

* \-   solid
* --  dashed
* -.  dashdot
* :   dotted
* "," None

#### 粗细
设置plot方法的关键字参数linewidth(或lw)可以改变线的粗细，其值为浮点数。

### marker
#### 各种参数分开设计
以下关键字参数可以用来设置marker的样式：

* marker
* markeredgecolor 或 mec
* markeredgewidth 或 mew
* markerfacecolor 或 mfc
* markerfacecoloralt 或 mfcalt
* markersize 或 ms

其中marker可取值为：

'.': point marker | ',': pixel marker | 'o': circle marker 
-|-|-
'v': triangle_down marker | '^': triangle_up marker | '<': triangle_left marker
'>': triangle_right marker | '1': tri_down marker | '2': tri_up marker
'3': tri_left marker | '4': tri_right marker | 's': square marker
'p': pentagon marker | '*': star marker | 'h': hexagon1 marker
'H': hexagon2 marker | '+': plus marker | 'x': x marker
'D': diamond marker | 'd': thin_diamond marker | '\|': vline marker
'_': hline marker | 

#### 各种参数整体设计
将各个参数放在一起，如

    plt.plot(x, y1, 'ro-')
    
## 图像窗口和布局
由于当前使用不多，因而在这里放置博客连接以供以后参考

<https://blog.csdn.net/C_chuxin/article/details/83994457>
