

## 1、introduce
this is a demo using cmake to configure and call dynamic library

## 2、CMakeLists.txt
```
CMAKE_MINIMUM_REQUIRED(VERSION 3.1)

# 1、指定项目名
project(demo_dylib)

# 2 、指定库所在的头文件 ${CMAKE_CURRENT_SOURCE_DIR}与CMakeLists.txt所在目录同级
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/ext/lib_hello/include)

# 3、指定库目录
link_directories(${CMAKE_CURRENT_SOURCE_DIR}/ext/lib_hello/build/lib) 

# 4、生成exe
add_executable(main src/main.cxx)

# 5、链接lib库
target_link_libraries(main hello_shared ) 

```


## 3、 tree of this demo
```
.
│  CMakeLists.txt
│  
├─build
├─ext
│  └─lib_hello
│      │  CMakeLists.txt
│      │  
│      ├─build
│      ├─include
│      │      hello.h
│      │      hi.h
│      │      
│      └─src
│              hello.cxx
│              hi.cxx
│              
└─src
        main.cxx

```

## 4、the order of command
A、configure dynamic library
* cd ext/lib_hello/build
* cmake ..
* make 

B、call dynamic library
    back to CMakeLists.txt directory 
* cd ../../
* cd build
* cmake ..
* make

