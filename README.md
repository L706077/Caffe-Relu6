# Caffe-Relu6
---

- [reference](https://github.com/RuiminChen/Caffe-MobileNetV2-ReLU6)

---
### Step 1.

***git clone or download frome [Caffe-MobileNetV2-ReLU6](https://github.com/RuiminChen/Caffe-MobileNetV2-ReLU6.git)*** ：
(1).
```C++
在 Caffe-MobileNetV2-ReLU6/目錄下：
  relu6_layer.cpp、
  relu6_layer.cu
拷貝到 $ YOUR_CAFFE_ROOT_PATH\src\caffe\layers 目錄裡
```
<br/>

(2).
```C++
在 Caffe-MobileNetV2-ReLU6/目錄下
relu6_layer.hpp
拷貝到 $ YOUR_CAFFE_ROOT_PATH\include\caffe\layers 目錄裡
```
<br/>


### Step 2.
***caffe.proto改寫：***

(1).
```C++
到$ YOUR_CAFFE_ROOT_PATH\src\caffe\proto 目錄裡打開"caffe.proto"
在 message LayerParameter {
...
}
裡面加入：
ReLU6Parameter relu6_param = 100000
```
<br/>

(2).
```C++
到$ YOUR_CAFFE_ROOT_PATH\src\caffe\proto 目錄裡打開"caffe.proto"
在最底下加入：
message ReLU6Parameter {
  optional float negative_slope = 1 [default = 0];
}
```
<br/>

### Step 3.
***重新編譯caffe.pb.cc caffe.pb.h:***
```C++
$ cd YOUR_CAFFE_ROOT_PATH/src/caffe/proto
$ protoc --cpp_out=/YOUR_CAFFE_ROOT_PATH/src/caffe/proto caffe.proto
$ cp /YOUR_CAFFE_ROOT_PATH/src/proto/caffe.pb.h /YOUR_CAFFE_ROOT_PATH/include/caffe/proto/caffe.ph.h
```

### Step 4.
***重新編譯caffe:***
```C++
$ cd  YOUR_CAFFE_ROOT_PATH
$ mkdir build
$ make 
$ make runtest
```





