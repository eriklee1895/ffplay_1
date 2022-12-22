cmake_minimum_required(VERSION 3.20)
project(ffplay_clion)

set(CMAKE_CXX_STANDARD 14)

## 添加头文件
include_directories(/usr/local/include)
include_directories(/usr/local/include/SDL2)

## 添加目标链接
link_libraries(/usr/local/lib/libSDL2.dylib)

find_package(PkgConfig REQUIRED)
pkg_check_modules(LIBAV REQUIRED IMPORTED_TARGET
        libavdevice
        libavfilter
        libavformat
        libavcodec
        libswresample
        libswscale
        libavutil
        )

# 执行编译命令
add_executable(${PROJECT_NAME} ffplay.c cmdutils.c opt_common.c)

target_link_libraries(${PROJECT_NAME}
        PkgConfig::LIBAV
        )
