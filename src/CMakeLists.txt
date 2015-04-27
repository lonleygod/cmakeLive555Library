# 添加头文件的查找目录  
INCLUDE_DIRECTORIES(../include)  

#MESSAGE(STATUS "opencv_dir:${OpenCV_DIR}")  

## 生成各种目标(target)文件: 可执行文件、动态库、静态库  
# 指定可执行文件的输出目录，输出到bin下面  
#SET(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)  
#SET(EXECUTABLE_OUTPUT_PATH ../bin)
# 指定可执行文件名(hello)和相关源文件   
#ADD_EXECUTABLE(adder main.cpp adder.cpp)  

ADD_DEFINITIONS(-DBSD=1 -DSOCKLEN_T=socklen_t -DHAVE_SOCKADDR_LEN=1 -DTIME_BASE=int)
#g++ -c  -I../include -I.  -DBSD=1 -O2 -DSOCKLEN_T=socklen_t -DHAVE_SOCKADDR_LEN=1 -DTIME_BASE=int GroupsockHelper.cpp

# 指定库文件输出路径  
SET(LIBRARY_OUTPUT_PATH ../../lib)  
#SET(LIBRARY_OUTPUT_PATH ../lib)

# 生成动态库  
# 注意，前面已经使用target文件名hello，这里不能再用。  
#ADD_LIBRARY(adder_dylib SHARED adder.cpp)  
# 设置库输出名为 hello => libhello.dylib  
#SET_TARGET_PROPERTIES(adder_dylib PROPERTIES OUTPUT_NAME "adder")
AUX_SOURCE_DIRECTORY(../src SRC_LIST)

# 生成静态库  
# 注意，前面已经使用target文件名hello，这里不能再用。  
ADD_LIBRARY(live555_a STATIC ${SRC_LIST})  
# 设置输库出名为 hello => libhello.a  
SET_TARGET_PROPERTIES(live555_a PROPERTIES OUTPUT_NAME "mylive555")  
