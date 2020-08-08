CMake Windows 编译/环境配置

# 注意项

```
HTTP_PROXY/HTTPS_PROXY // cmake编译中需要下载文件

下载https://github.com/opencv/opencv_contrib/releases并解压后配置到OPENCV_EXTRA_MODULES_PATH = */modules
```

# 编译
```
cmake -B ../build -G "Visual Studio 16 2019" -A x64 -DCMAKE_INSTALL_PREFIX=../install -DBUILD_opencv_world=true -DOPENCV_EXTRA_MODULES_PATH=../contrib/modules
```

# env

```
PATH=*;*\install\x64\vc16\bin
OpenCV_DIR=*\install\x64\vc16\lib
```
