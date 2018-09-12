## 有方N20模组

------

N20 是一款基于高通平台的工业级模块，模块支持 eMTC(Cat M1)， NB-IoT(Cat NB1)，
GSM/GPRS/EDGE， GNSS(GPS/GLONASS/BDS)

- ARM Cortex-A7 处理器， 1.3 GHz 主频， 256kB L2 缓存， 28nm 工艺
- 支持网络类型： Cat M1/Cat NB1/GSM/GNSS
- 支持 USB2.0/UIM/ADC/UART/SPI/I2C/PCM/SDIO/GPIO

## N20入网测试

------

1. #### 上电，单击PWRKEY按键，模组启动

   `AT`

   返回：

   `OK`

2. #### 确定SIM卡连接正常

   `AT+CCID`

   返回：

   `+CCID: 898607B119179406××××`

3. #### 网络状态

   **查询**

   `AT+NETSTATE?`

   返回：

   `+NETSTATE: 0,0x80`

   `0`是CAT NB1网络，`0x80`是LTE B5频段

   **设置**

   `AT+NETCFG="netmode",2`

   `AT+NETCFG="netpri",0`

   `AT+NETCFG="netband",0x10`

4. #### 网络注册状态

   `AT+CEREG?`

   这个指令返回的结果，可能有以下几种，这里详细的说一下：

   `+CEREG:0,0`

   `+CEREG:0,1`

   `+CEREG:0,2`

   前面一个0，是功能码，如果设置为0，只有我们请求的时候才会返回+CEREG这个结果，设为1，一旦网络状态发生改变的时候，会自动上报URC来通知我们。

   后面的0,1,2，当为0的时候，说明网络还未注册，依旧在搜索信号，一般刚开机的时候，发送请求会返回为0，当为1的时候，这个时候表明网络已经注册成功了，可以正常使用了。如果为2的时候，这个是从0到2的转换，再次尝试入网，这个时候就说明网络质量或者线路并不是很流畅，模组在尝试入网。如果一直为2的话，建议重启模组或重启射频CFUN。直至返回结果为+CERGE:0,1。当然后面还有3,4,5等，这些目前都用不到。

5. #### 创建TCP连接

   `AT+XIIC=1`

   返回：

   `OK`

   `AT+TCPSETUP=0,106.15.100.2,1883`

   返回：

   `OK`

   `+TCPSETUP: 0,OK`


