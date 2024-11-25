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
add_executable(Hello_world Hello_world.cpp)
```

如果要设定输出可执行文件的路径(当前目录为编译文件的目录)，可以

```cmake
set(EXECUTABLE_OUTPUT_PATH ./output)
```

## 2. 多文件编译

在一个文件夹里文件非常多时，可以将它们保存到一个变量中

```cmake
aux_source_directory(. SRC_LIST)
```
第一个参数是目录，第二个参数是变量名

增加新的头文件搜索目录

```cmake
include_directories(<dir>)
```
**将文件纳入执行文件目录后，CMake就会在build过程自动编译并生成可执行文件**

生成一个静态库或动态库

```cmake
add_library(func_shared SHARED ${SRC_LIST})
add_library(func_static STATIC ${SRC_LIST})
```
第一个参数是名称，第二个参数是类型，第三个参数是源文件

设置库文件输出路径

```cmake
set(LIBRARY_OUTPUT_PATH ${PROJECT_BINARY_DIR}/../lib)
```

修改库输出名称，这里将其统一命名为myfunc

```cmake
set_target_properties(func_shared PROPERTIES OUTPUT_NAME "myfunc")
set_target_properties(func_static PROPERTIES OUTPUT_NAME "myfunc")
```

链接库文件到可执行文件

```cmake
find_library(func_lib myfunc ${PROJECT_BINARY_DIR}/../lib)
target_link_libraries(Hello_world ${func_lib})
```

第一个函数将在指定目录下寻找myfunc库，并将其储存在func_lib变量中。

第二个函数将库文件链接到可执行文件中。


## 参考

[CMake官方文档](https://cmake.org/cmake/help/latest/index.html)

[中文文档](https://modern-cmake-cn.github.io/Modern-CMake-zh_CN/chapters/basics.html)

[参考文档](https://blog.csdn.net/iuu77/article/details/129229361)