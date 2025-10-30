# windows_lvgl8
## 说明
关于LVGL模拟器的说明
## 运行环境
- 需要 cmake
- 需要c编译环境
- 需要sdl库的支持
### windows的cmake安装
- 官网的下载地址为 (https://cmake.org/download/)
- 在Binary distributions  下找：这是二进制文件，也就是官方帮你编译好的可以直接执行的文件
- Windows x64 Installer 为安装版(后缀.msi)；  Windows x64 ZIP(后缀.zip)   非安装版
- 安装版直接安装即可，非安装版 需要自己到 我的电脑->属性->高级系统设置->环境变量->系统变量->Path添加路径
- 路径例如 D:\software\cmake-3.27.1-windows-x86_64\bin
- 安装完成后，打开windows命令行 输入如下命令测试 : `cmake --version` 会看到如下信息，表示成功，否则失败
```sh
cmake version 3.30.0
CMake suite maintained and supported by Kitware (kitware.com/cmake).
```
- 附一个下载链接，是我常用的cmake 版本(https://www.123865.com/s/CI9ITd-rtEY3)


## windows的c编译环境安装
- windows不同于linux，本身并不具备c的编译环境，所以需要单独安装mingw以支持c编译环境
- 下载地址(https://sourceforge.net/projects/mingw-w64/files/mingw-w64/mingw-w64-release/)
- 版本有很多，我不解释了，有兴趣自己查区别
- 这里我提供一个我常用的版本(https://www.123865.com/s/CI9ITd-8tEY3)
- 解压后需要添加环境变量 ：我的电脑->属性->高级系统设置->环境变量->系统变量->Path添加路径
- 路径例如 `D:\software\mingw64\bin`
- 安装完成后，打开windows命令行 输入如下命令测试 : `gcc --version` 会看到如下信息，表示成功，否则失败
```sh
gcc (x86_64-win32-sjlj-rev0, Built by MinGW-W64 project) 8.1.0
Copyright (C) 2018 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

## SDL库的支持添加
- github下载地址为(https://github.com/libsdl-org/SDL)
- 这里我提供一个我常用的版本(https://www.123865.com/s/CI9ITd-0tEY3)
- 下载完成后，把sdl下 的cmake 整个文件夹 解压到 mingw目录下
- 把sdl下的 x86_64-w64-mingw32 整个解压到mingw目录下





## 编译方法
- 进入 lv_port_pc 下的 build 文件夹 下按住shift 点击鼠标右键，打开powershell
- 输入 `cmake -G "MinGW Makefiles" .. ` 回车
- 输入mingw 按tab 补齐。会有 ` mingw32-make.exe` 直接执行，开始编译
- 编译成功，会在 工程目录\bin 下生成一个可执行文件，运行会报错说找不到 SDL2.dll , 把前面下载的SDL压缩包找到SDL2.dll复制到可执行文件的同一目录即可









# 移植过程
本例已经是移植好的例子，不需要再移植，如果需要了解完整过程，如下说明。
## 下载 LVGL源码 
- 官方地址(https://github.com/lvgl/lvgl/tags)
- 我选择lvgl 8.4
## 下载 drives 代码
- 官方地址(https://github.com/lvgl/lv_drivers/tags)
## 下载工程源码
- 官方地址(https://github.com/lvgl/lv_port_pc_eclipse/tags)

## 个人链接
- 链接如下 (https://www.123865.com/s/CI9ITd-VCEY3)

## lvgl 文件移植
- 解压lv_port_pc_eclipse-8.2.0.zip 得到 lv_port_pc_eclipse
- 把lvgl源码解压，把文件夹名改为lvgl ,替换到 lv_port_pc_eclipse 下
- 把 lv_drives 解压，把文件夹名改为lv_drivers ,替换到 lv_port_pc_eclipse 下
- 打开 lv_conf.h 修改 LV_GRAD_CACHE_DEF_SIZE为512 避免报错
- 如果运行提示错误 **lv_timer_handler: It seems lv_tick_inc() is not called** ，那就在while 循环中添加 `lv_tick_inc(5);`






