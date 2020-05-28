# 1. 传感器类
## (1) Sensor 类
功能:传感器的运行时的主程序,记录了设备的相关信息,并通过
计时器实现自律化操作

## (2) Parameter 类
功能:数据记录的抽象类,记录测量的的结构,负责与物理传感器的交互操作
### 1. measureParameter()
功能:获取实时的环境参数信息
### 2. calibration()
功能:校准所连接的传感器

## (3)Request Parameter 接口
功能:为外部的设备直接调用传感器设备信息以及测量结果提供接口
### 1. setDeviceID(long)
功能:从外部改变设备的 ID
输入:新的 long 型设备 ID
### 2. getParameter()
功能:获得此时的测量数据
输出:返回 JSON 格式的文件
### 3. getDevicID()
功能:获取设备 ID
输出:long 型设备 ID
### 4. restartDevice()
功能:重新启动传感器设备
