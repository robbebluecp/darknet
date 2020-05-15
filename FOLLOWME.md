
1、安装依赖  
get -y install libprotobuf-dev libleveldb-dev libsnappy-dev libopencv-dev libhdf5-serial-dev protobuf-compiler  
get -y install --no-install-recommends libboost-all-dev  
get -y install libopenblas-dev liblapack-dev libatlas-base-dev  
get -y install libgflags-dev libgoogle-glog-dev liblmdb-dev  
get -y install git build-essential unzip
apt -y install zlib* libssl-dev bzip*
apt -y install git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev

2、安装cmake（相对比较新的）  
（1）下载  
* wget https://lzy-public-data.oss-cn-beijing.aliyuncs.com/cmake-3.15.5.tar.gz
（2）安装
* tar -zxf cmake-3.15.5.tar.gz
* cd cmake-3.15.5/ & .configure
* make
* make install  

2、安装cuda和cudnn
* https://blog.csdn.net/sinat_23853639/article/details/80990967
* 或者你买服务器吧- - 切记，cuda >= 10.0

3、安装opencv
* wget https://lzy-public-data.oss-cn-beijing.aliyuncs.com/opencv-4.3.0.zip
* https://blog.csdn.net/qq_36486890/article/details/97511295

4、安装darknet
* 没有安好以上所有东西的，别往下继续了
* cd /opt
* git clone https://github.com/robbebluecp/darknet.git
* ./build.sh

5、现在你可以开始训练自己的数据了，我提供了一份整理好的voc数据
* cd /opt
* wget https://lzy-public-data.oss-cn-beijing.aliyuncs.com/voc2007.zip
* unzip voc2007.zip
* cd /opt/darknet
* ./darknet cfg/train_meta.data cfg/train_net.cfg -dont_show    # 正常训练
* ./darknet cfg/train_meta.data cfg/train_net.cfg yolov4.conv.137 -dont_show    # 加载预训练模型训练 【wget https://lzy-public-data.oss-cn-beijing.aliyuncs.com/yolov4.conv.137】
* ./darknet detector train cfg/train_meta.data cfg/train_net.cfg yolov4.conv.137 -dont_show -map -json_port 1000 -mjpeg_port 1001 # 输出训练结果到1001端口
* ./darknet cfg/train_meta.data cfg/train_net.cfg  backup/xxx.weighst -dont_show    # 断点训练

6 预测
* step to https://github.com/robbebluecp/keras-yolo4-core
