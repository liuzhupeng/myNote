Windows下虚拟机安装Mac OS X —– VMware Workstation12安装Mac OS X 10.11

本文即将介绍WIN虚拟MAC的教程。完整详细教程（包含安装中的一些问题）

【并且适用其他mac os x版本】

更多资源：http:\/\/blog.sina.com.cn\/lr34

## 工具\/原料

* Mac OS X 10.11 镜像文件（链接：http:\/\/pan.baidu.com\/s\/1pL8HE59 密码：cq4d）（此镜像为网络收集，如果觉得有问题自己找谢谢。）
* unlocker208文件（链接：http:\/\/pan.baidu.com\/s\/1bpftVjT 密码：dp2g）
* VMware Workstation12（http:\/\/blog.sina.com.cn\/s\/blog\_af49f8090102wqmw.html）

## 方法\/步骤

1. 1
  首先下载安装 vmware workstation12，先不忙运行软件。

2. 2
  下载解压unlocker208文件，找到点击运行**win-install.cmd。**

  _**这一步很关键，否则vm12就无法识别OS X系统**_

3. 3
  然后打开运行vmware workstation12，选择创建新的虚拟机

4. 4
  选择典型，然后下一步

5. 5
  选择安装程序光盘映像文件，点击选择CDR镜像文件路径 .

  （**当然你也可以自己是用自己的镜像。但是最好是下载后缀名为cdr的**）

6. 6
  选择Apple Mac OS X ，然后选择OS X 10.11 版本

  **如果第二步unlocker文件没有处理好的话，这个地方可能就不会出现Apple Mac OS X。如果不行，可以多下载几个unlocker试试。**

7. 然后依次根据**新建虚拟机向导**提示选择，最后完成创建。

8. 然后点击开启虚拟机

9. 首次运行时，会出现错误提示。这时不要着急。

  关闭运行的虚拟机。

10. 找到在之前的创建新的虚拟机时，**设置的虚拟机位置**。打开该目录，找到**OS X xx.xx.vmx**文件（这里的文件是：OS X 10.11.vmx），右键用记事本方式打开，找到** smc.present = “TRUE”**

11. 在**smc.present = “TRUE”**后面，手动添加一句**smc.version = 0**

  然后保存关闭，再重新启动虚拟机，就不会报错了。

12. 若果在安装中出现**蓝屏boot manager的现象，**一般都是跟下载的**镜像文件有问题导致**。建议你可以重新找些cdr镜像文件。

  我这里提供的镜像文件已经测试过，完美通过。

13. 最后根据安装向导提示安装操作。然后到安装OS Ｘ时，会提示“**ＯS X Base System”没有足够空间安装**

14. 这时点击屏幕上方的**实用工具**选项。选择“**磁盘工具**”。选中**vmware workstation SATA hard drive media。**

15. 选择** 抹除 **选项，格式选择**OSＸ扩展日志式** ，方案选择 **ＧＵＩＤ。**

  **抹除后，退出**磁盘工具

16. 这时会再次在安装ｏｓｘ ，这时会出多出现一个盘符，选择这个盘安装

  [步骤阅读](http://jingyan.baidu.com/album/363872ec206a356e4ba16f30.html?picindex=20)
17. 17
  后面就没什么问题。慢慢等待安装成功！！！！！！


