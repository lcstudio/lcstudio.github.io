1. 安装依赖包

apt-get install libprotobuf-dev libleveldb-dev libsnappy-dev libopencv-dev libhdf5-serial-dev protobuf-compiler libatlas-base-dev libgflags-dev libgoogle-glog-dev liblmdb-dev
apt-get install --no-install-recommends libboost-all-dev

2. 修改编译脚本

> Makefile.config文件
```text
INCLUDE_DIRS := $(PYTHON_INCLUDE) /usr/local/include /usr/include/hdf5/serial/
```
多gpu训练添加nccl工具

> Makefile文件修改

```text
LIBRARIES += hdf5_hl hdf5
LIBRARIES += hdf5_serial_hl hdf5_serial
```

3. 测试mnist项目

sudo sh ./data/mnist/get_mnist.sh
./examples/mnist/create_mnist.sh
./build/tools/caffe train --solver=examples/mnist/lenet_solver.prototxt
