------

首先 简单地介绍一下什么是cmake. 
> cmake是一个用于管理代码构建的工具. 支持跨平台, 主要用于C/C++代码构建

简而言之, cmake 本身就是用于构建代码并最终生成目标可执行文件 exe、静态库(.lib .a)或者动态库(.dll .so) 的工具.

话不多说 实战为先.  首先我们来用cmake 搭建一个 最简单的程序: 
打印 **hello cmake !**

#### 起步：尝试着构建第一个程序吧

##### main.cpp
```c++
#include <iostream>

int main()
{
   std::cout << "hello cmake !" << std::cout;
   return 0;
}
```

##### CMakeLists.txt
```cmake
cmake_minimum_required(VERSION 3.4.1)

project(hello_cmake)

add_executable(hello_cmake main.cpp)
```

CMakeList.txt 你可以将其想象为一个用cmake语法写出的脚本文件, 通过执行这个脚本就能完成项目的构建工作.

那么, 本次示例中的CMakeLists.txt每一行都有什么意义呢?

1. `cmake_minimum_required(VERSION 3.4.1)`: 设置当前cmake脚本所支持的最低cmake版本.
2. `project(hello_cmake)`： 开启一个新的cmake项目. 这将触发许多内部CMake逻辑，尤其是对默认C和C ++ 编译器的检测.
3. 通过 `add_executable(hello_cmake main.cpp)`  创建一个构建目标. 使用当前编译器的配置 从源文件 main.cpp 中编译出目标可执行程序.

可以看出 cmake 执行完毕后会生成一个 名为 hello_cmake 的 project, 这个project 编译通过后会生成一个 名为 hello_cmake 的目标可执行程序.

##### 命令行构建程序

这里将我们的目录结构分配如下:
> main.cpp
> CMakeLists.txt
> build\


注意这里的 build 是一个我们新建的空目录(为什么新建一个空build目录后面会讲). 然后我们执行如下command:
```cmd
cd build
cmake ..
cmake --build .
```


\执行完毕上述命令后, 我们就会在build目录中发现已经编译完成的project. 目录结构大概如下: 
> 

找到我们生成的可执行文件, 默认的是放在 Debug 目录中

```
./hello_cmake
hello cmake !
```

到这里我们已经成功地使用cmake构建并运行出第一个程序了哦~





知其然知其所以然.  这里我们在 执行了这些命令的同时发生了 什么?

小贴士: 