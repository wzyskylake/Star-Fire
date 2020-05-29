# 1. 传感器类
## 1.1 Sensor 类
功能:主要负责传感器部分运行,可以被主机设备接入并设置设备号
### Sensor Interface 接口
#### setDeviceID(long)
功能:设置传感器设备的 ID,方便明确数据采集对象  
输入:long 型设备 ID 
#### getParameter()
功能:生成包含环境参数信息的比特流,并向外部设备发送  
输出:规定格式的比特流
#### getDeviceID()
功能:为外部设备提供设备 ID  
输出:long 型设备 ID 
#### measureParameter()
功能:立即从串口获取传感器测量得到的环境参数,存入对象缓存区中  
输出:True--测量成功;False--测量失败
#### restartDevice()
功能:重启传感器设备,并清除相应缓冲区  
输出:True--重启成功;False--重启失败
## 1.2 Mainframe 类
功能:主机设备通过内部定时器执行循环操作,即从所连接的传感器设备读取参数信息(比特流),解析并向服务器发送得到数据;同时接收服务器的控制命令,通过连接的控制器来执行控制操作
#### calculagraph()
功能:作为内部计时器,定时激活相应内部操作
### Mainfarme Interface 接口
#### setDeviceID(long)
功能:设置传感器设备的 ID,在新增设备并入网络后由服务器设置设备信息  
输入:long 型设备 ID 
#### getDeviceID()
功能:为服务器设备提供设备 ID
输出:long 型设备 ID 
#### getData()
功能:为服务器提供获取主机设备记录数据的接口  
输出:JSON 格式包含了主机设备信息以及设备信息的文件
#### addSensor()
功能:在总线上新增传感器设备后,执行此函数,完成记录连接设置等操作
输出:True--添加成功;False--添加失败
#### restartDevice()
功能:功能:重启传感器设备,但不清除连接设备的记录信息
## 1.3Controller 类
功能:控制所连接控制设备,检测设备的运行状态,为主机设备执行控制命令
#### setOrder()
功能:服务器向控制器发送控制指令来控制环境
输入:包含控制信息的 JSON 文件
输出:返回接收确认信息
#### getInformation()
功能:服务器获取控制器运行信息
输出:包含运行信息的 JSON 文件
#### emergencyStop()
功能:在发生紧急情况时停止一切控制器件的操作
### 1.3.1 Fan 类
#### speedUP()
功能:增加风扇转速
#### speedDown()
功能:降低风扇转速
### 1.3.2 Light 类
#### turnON()
功能:开启照明
#### turnOFF()
功能:关闭照明
### 1.3.3 Pump 类
#### srartWork()
功能:开启水泵
#### stopWork()
功能:关闭水泵
### 1.3.4 Air Condition 类
#### srartWork()
功能:开启空调
#### stopWork()
功能:关闭空调