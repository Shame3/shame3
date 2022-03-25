向orb_slam2 中添加语义约束. 
具体表现在给每个特征点,地图点添加label(class_id来自语义分割图对应位置的像素值)
在赋予label时考察周围像素点信息.
具体修改:Frame.cc 中ExtractORBNew 函数,ORBmatcher.cc ,输入函数等
在FrameDrawer.cc 修改帧的绘制函数发现问题,使用opencv 的circle ,rectangle 函数绘制
特征点总是位置不匹配问题,如果直接给像素值赋值是可以的(也不知道谁是正确的),使用rgb 图像修改像素值也不可行,目前是使用灰度图直接修改像素值bug 还在排查中.目前不好测试,只能目测审视代码...
使用的话需要配合修改mono_kitty.cc 中的路径.建议image_0 与 语义分割图文件夹放一起,运行时需要修改run.sh 最后的路径
