新增了对交换芯片RTL8367S的支持，相关的机型为以MTK7620A/DA为主控外接交换芯片实现千兆有线的水星D12G，Tplink C5 v4等等  
源码来自于https://gitlab.com/dm38/padavan-ng  
相关提交为https://gitlab.com/dm38/padavan-ng/-/commit/4ec2acb96dccc268ec23aa71b8f5fcb283b9e122  
  
新增了对xtls的支持，源码来自于xumng123  
https://github.com/xumng123/rt-n56u  
感谢vb1980持续对代码做出的测试和改进，他在原本的基础上新增了对xray的编译，而我之前就直接替换了v2ray的bin，所以是殊途同归啦  
https://github.com/vb1980/Padavan-KVR  
  
# Padavan
基于hanwckf,chongshengB以及padavanonly的源码整合而来，支持kvr  
编译方法同其他Padavan源码，主要特点如下：  
1.采用padavanonly源码的5.0.4.0无线驱动，支持kvr  
2.添加了chongshengB源码的所有插件  
3.其他部分等同于hanwckf的源码，有少量优化来自immortalwrt的padavan源码  
4.添加了MSG1500的7615版本config  
  
以下附上他们四位的源码地址供参考  
https://github.com/hanwckf/rt-n56u  
https://github.com/chongshengB/rt-n56u  
https://github.com/padavanonly/rt-n56u  
https://github.com/immortalwrt/padavan  

已测试的机型为MSG1500-7615，JCG-Q20，CR660x  
  
固件默认wifi名称
 - 2.4G：机器名_mac地址最后四位，如K2P_9981
 - 5G：机器名_5G_mac地址最后四位，如K2P_5G_9981

wifi密码
 - 1234567890

管理地址
 - 192.168.2.1

管理账号密码
 - admin
 - admin

**最近的更新代码都来自于hanwckf和MelsReallyBa大佬的4.4内核代码**
- https://github.com/hanwckf/padavan-4.4
- https://github.com/MeIsReallyBa/padavan-4.4

- 已适配除官方适配外的以下机型
>- PSG1208
>- PSG1218
>- 5K-W20 (USB)
>- OYE-001 (USB)
>- NEWIFI-MINI (USB)
>- MI-MINI (USB)
>- MI-3 (USB)
>- MI-3C
>- MI-4
>- MI-R3G (USB)
>- MI-R4A
>- MI-R3P (USB)
>- HC5661A
>- HC5761A (USB)
>- HC5861B
>- 360P2 (USB)
>- MI-NANO
>- MZ-R13
>- MZ-R13P
>- RT-AC1200GU (USB)
>- XY-C1 (USB)
>- WR1200JS (USB)
>- NEWIFI3 (USB)
>- B70 (USB)
>- A3004NS (USB)
>- K2P
>- K2P-USB (USB)
>- JCG-836PRO (USB)
>- JCG-AC860M (USB)
>- DIR-882 (USB)
>- DIR-878
>- MR2600 (USB)
>- WDR7300
>- RM2100
>- CR660x (CR6606, CR6608, CR6609)
>- R2100
>- JCG-Y2 (USB)
>- E8820V2 (USB)
>- ZTE_E8820S (USB)
>- MSG1500 (USB)
>- R6220 (USB)
>- NETGEAR-CHJ (R6260, R6350, R6850, WAC124)
>- NETGEAR-BZV (R6800, R6700-v2, R7200, Nighthawk AC2400)

***

### 编译说明 ###

* 安装依赖包

```shell
# Debian/Ubuntu
sudo apt update
sudo apt install unzip libtool-bin curl cmake gperf gawk flex bison nano xxd \
	fakeroot kmod cpio git python-docutils gettext automake autopoint \
	texinfo build-essential help2man pkg-config zlib1g-dev libgmp3-dev \
	libmpc-dev libmpfr-dev libncurses5-dev libltdl-dev wget libc-dev-bin

# cd /usr/local/src
# sudo wget http://ftp.gnu.org/gnu/texinfo/texinfo-6.7.tar.gz
# sudo tar zxvf texinfo-6.7.tar.gz
# cd texinfo-6.7
# sudo ./configure
# sudo make
# sudo make install

```

* 克隆源码

```shell
git clone --depth=1 https://github.com/xiaiohuan/Padavan-KVR.git /opt/Padavan-KVR
```

* 准备工具链

```shell
cd /opt/Padavan-KVR/toolchain-mipsel

# （推荐）使用脚本下载预编译的工具链：
sh dl_toolchain.sh

# 或者，也可以从源码编译工具链，这需要一些时间：
./clean_toolchain
./build_toolchain

```

* (可选) 修改机型配置文件

```shell
nano /opt/Padavan-KVR/trunk/configs/templates/K2.config
```

* 清理代码树并开始编译

```shell
cd /opt/Padavan-KVR/trunk
./clear_tree
fakeroot ./build_firmware_modify MI-R3
# 脚本第一个参数为路由型号，在trunk/configs/templates/中
# 编译好的固件在trunk/images里
```

***

### 请参阅 ###
- https://www.jianshu.com/p/cb51fb0fb2ac
- https://www.jianshu.com/p/6b8403cdea46

### 特别说明 ###
* hanwckf源码：https://github.com/hanwckf/rt-n56u
* lean源码: https://github.com/coolsnowwolf/lede
* 汉化字典来自：https://github.com/gorden5566/padavan
* hanwckf更新日志：https://www.jianshu.com/p/d76a63a12eae


