# Dell-Inspiron-7579-Hackintosh
 
## System configuration
|Model	|MacBookPro16,1	|Version	|BigSur 11.3|
| :----- | :----- |:----- |:----- |
|Processor |Intel Core i5-7200U	|Graphics	|Intel HD Graphics 620|
|Memory	   |2400MHz DDR4 24GB	|OS Disk	|SK Hynix SC308 256GB|
|Audio	   |Realtek ALC3253	|WiFi/Bluetooth	|3165AC|
|BIOS      |Dell Inc. 1.28.0    |

## 解锁CFG Lock
|Setting item|Var Store|Variable|Initial value|Modify value|
| :----- | :----- |:----- |:----- |:----- |
| CFG Lock|CpuSetup|0x4C7|0x01|0x00 |

 -  官网下载BIOS
 https://www.dell.com/support/home/
 -  把固件包丢到``Dell_PFS_Extract``解压BIOS更新程序

 -  用``UEFITool``程序打开解压目录下的``System BIOS with..``文件

 -  按``Ctrl+F``查找 在``GUID``选项下选中``Header only``然后再输入``899407D799FE43D89A2179EC328CAC21`` 

 -  双击Search查询结果,在Steup行右键另存 会得到一个``File_DXE_driver_Setup.ffs``文件

 -  用``IRFExtractor``解压``File_DXE_driver_Setup.ffs``文件

 -  在解压下来的文件文件里面查询``CFG``对应的值

 -  以下操作存在风险,如若不懂切勿自行操作
 
 -  把U盘FAT32格式化，把``bootx64.efi``文件放进BOOT目录下(目录``\EFI\BOOT\``)，开机U盘启动

 -  在grub>输入 ``setup_var 0x4C7``回车  (后面的0x4C7是刚才前面查到的CFG值）返回结果``offset 0x4C7 is: 0×01``

 -  然后输入``setup_var 0×5A4 0×00 ``回车 

 - 再次输入 ``setup_var 0x4C7``回车 返回结果``offset 0x4C7 is: 0×00`` （成功）

 - 需要的工具 
```
链接: https://pan.baidu.com/s/1CtR8Ey7Hdx9vuKI3mq77XQ 
提取码: 3iyh
```

## 工具
|名称|网址|下载
| :----- | :----- |:----- |
|DiskGenius |https://www.diskgenius.cn| https://www.diskgenius.cn/download.php |
|balenaEtcher |https://www.balena.io/etcher| https://www.balena.io/etcher |
|OpenCore |https://github.com/acidanthera| https://github.com/acidanthera/OpenCorePkg/releases |
|QtOpenCoreConfig|https://github.com/ic005k| https://github.com/ic005k/QtOpenCoreConfig/releases |
|MacInfoPkg|https://github.com/acidanthera/| https://github.com/acidanthera/MacInfoPkg/releases 
|AppleSupportPkg|https://github.com/acidanthera/| https://github.com/acidanthera/AppleSupportPkg/releases 
|Hackintool|| http://headsoft.com.au/download/mac/Hackintool.zip |


## Dell Inspiron 15-7579 Settings 


| System Configuration |SATA Operation|AHCI|硬盘模式|
| :----- | :----- |:----- |:----- |
| System Configuration | Miscellaneous Devices  |Enable Secure Digital (SD)Card |关闭SD读卡器|
| Secure Boot |Secure Boot Enable  |Disabled |关闭安全启动|

开机按“F2”，进入到Bios界面，修改bios ：
+ 1、Secure Boot - Secure Boot Enable里改成Disabled
+ 2、General - Advanced Boot Options里，Enable Legacy Option ROMs勾上
+ 3、System Configuration - SATA Operation 改成 AHCI
+ 4、Boot Sequence - Boot List Option设置为UEFI


## N. Log
+ [黑果小兵](https://blog.daliansky.net)
+ [Xjn´s Blog](https://blog.xjn819.com/post/opencore-guide.html)
+ [精解OpenCore](https://blog.daliansky.net/OpenCore-BootLoader.html)
+ [ Inspiron-7579](https://github.com/ashishcomputing/Dell-Inspiron-7560-Hackintosh-Opencore)
+ [Dell-7560](https://oc.skk.moe/)
+ [OpenCore 参考手册](https://oc.skk.moe/)
+ [主板BIOS设置](https://www.bilibili.com/video/BV1rJ411r7Jt)
+ [Dell Inspiron 15 7579 2-in-1](https://www.dell.com/support/home/zh-cn/product-support/servicetag/0-elU0cHBkNVcwd0JDODZkMlFTSDl6dz090/overview)
+ [BIOS](https://www.jianshu.com/p/e490108cd6e6)
+ [Dell-7579-CFG解锁指导](https://www.bilibili.com/video/av714357334/)
+ [主板解锁CFG LOCK教程](https://www.bilibili.com/read/cv6167464)
