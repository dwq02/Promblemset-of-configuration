## 1. 开始一个CMake文件

开始CMake文件前，需要指定CMake所允许的最低版本

```cmake
cmake_minimum_required(VERSION 3.31)
```

接着，需要声明工程的名字

```cmake
project(myCMake)
```

将所需要编译执行的文件加入进来

```cmake
add_executable(CMakename Hello_world.cpp)
```

如果要设定输出可执行文件的路径(当前目录为编译文件的目录)，可以

```cmake
set(EXECUTABLE_OUTPUT_PATH ./output)
```

## 参考

[CMake官方文档](https://cmake.org/cmake/help/latest/index.html)

[中文文档](https://modern-cmake-cn.github.io/Modern-CMake-zh_CN/chapters/basics.html)

[参考文档](https://blog.csdn.net/iuu77/article/details/129229361)