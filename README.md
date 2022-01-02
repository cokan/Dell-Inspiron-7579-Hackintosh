# Dell-Inspiron-7579-Hackintosh
 
##System configuration
|Model	|MacBookPro16,1	|Version	|BigSur 11.3|
| :----- | :----- |:----- |:----- |
|Processor |Intel Core i5-7200U	|Graphics	|Intel HD Graphics 620|
|Memory	   |2400MHz DDR4 24GB	|OS Disk	|SK Hynix SC308 256GB|
|Audio	   |Realtek ALC3253	|WiFi/Bluetooth	|3165AC|
|BIOS      |Dell Inc. 1.28.0    |

[button color="dark" icon="" url="https://www.dell.com/support/home/zh-cn/product-support/servicetag/0-elU0cHBkNVcwd0JDODZkMlFTSDl6dz090/overview#" type="round"]Dell Inspiron 15 7579 2-in-1[/button] 
##解锁CFG Lock
| :----- | :----- |:----- |:----- |
|名称	|偏移量	|默认值(开启)	|修改值(关闭)
|CFG Lock|0x4C7|0x01|0x00

[collapse status="false" title="Dell-7579-CFG解锁指导 ``存在严重风险,切勿随意操作``"]
[button color="info" icon="" url="https://www.bilibili.com/video/av714357334/" type="round"]视频[/button]  [button color="danger" icon="" url="https://www.bilibili.com/read/cv6167464/" type="round"]教程[/button]

 -  官网下载BIOS
 https://www.dell.com/support/home/
 -  把固件包丢到``Dell_PFS_Extract``解压BIOS更新程序
![解压][1]
 -  用``UEFITool``程序打开解压目录下的``System BIOS with..``文件
![UEFITOOL][2]
 -  按``Ctrl+F``查找 在``GUID``选项下选中``Header only``然后再输入``899407D799FE43D89A2179EC328CAC21`` 
![查找CFG][3] 
 -  双击Search查询结果,在Steup行右键另存 会得到一个``File_DXE_driver_Setup.ffs``文件
![保存CFG][4]
 -  用``IRFExtractor``解压``File_DXE_driver_Setup.ffs``文件
![IRFExtractor][5]
 -  在解压下来的文件文件里面查询``CFG``对应的值
![查询CFG][6]![CFG值][7]
[scode type="red"]以下操作存在风险,如若不懂切勿自行操作[/scode]
 -  把U盘FAT32格式化，把``bootx64.efi``文件放进BOOT目录下(目录``\EFI\BOOT\``)，开机U盘启动
![目录][8]
 -  在grub>输入 ``setup_var 0x4C7``回车  (后面的0x4C7是刚才前面查到的CFG值）返回结果``offset 0x4C7 is: 0×01``
![查询][9]
 -  然后输入``setup_var 0×5A4 0×00 ``回车 
![修改][10]
 - 再次输入 ``setup_var 0x4C7``回车 返回结果``offset 0x4C7 is: 0×00`` （成功）
![修改成功][11]
 - 需要的工具 
```
链接: https://pan.baidu.com/s/1CtR8Ey7Hdx9vuKI3mq77XQ 
提取码: 3iyh
```
[/collapse]

##工具
|名称|网址|下载
| :----- | :----- |:----- |
|DiskGenius |https://www.diskgenius.cn|[button color="info" icon="" url="https://www.diskgenius.cn/download.php" type=""]下载地址[/button]|
|balenaEtcher |https://www.balena.io/etcher|[button color="info" icon="" url="https://www.balena.io/etcher" type=""]下载地址[/button]|
|OpenCore |https://github.com/acidanthera|[button color="info" icon="" url="https://github.com/acidanthera/OpenCorePkg/releases" type=""]下载地址[/button]|
|QtOpenCoreConfig|https://github.com/ic005k|[button color="info" icon="" url="https://github.com/ic005k/QtOpenCoreConfig/releases" type=""]下载地址[/button]|
|MacInfoPkg|https://github.com/acidanthera/|[button color="info" icon="" url="https://github.com/acidanthera/MacInfoPkg/releases" type=""]下载地址[/button]
|AppleSupportPkg|https://github.com/acidanthera/|[button color="info" icon="" url="https://github.com/acidanthera/AppleSupportPkg/releases" type=""]下载地址[/button]
|Hackintool||[button color="info" icon="" url="http://headsoft.com.au/download/mac/Hackintool.zip" type=""]下载地址[/button]|

[button color="black" icon="" url="https://blog.daliansky.net/" type=""]黑果小兵[/button] [button color="primary" icon="" url="https://blog.xjn819.com/post/opencore-guide.html" type=""]Xjn´s Blog[/button] [button color="info" icon="" url="https://blog.daliansky.net/OpenCore-BootLoader.html" type=""]精解OpenCore[/button] [button color="black" icon="" url="https://github.com/ayive/Dell-Inspiron-7579-Hackintosh" type=""] Inspiron-7579[/button] [button color="warning" icon="" url="https://github.com/ashishcomputing/Dell-Inspiron-7560-Hackintosh-Opencore" type=""] Inspiron-7560[/button] [button color="primary" icon="" url="https://github.com/LinBiaoGe/Dell-7560-Hackintosh-OC/" type=""]Dell-7560[/button] [button color="primary" icon="" url="https://oc.skk.moe/" type=""]OpenCore 参考手册[/button]


[collapse status="false" title="修改 hosts 加速Github"]
[post cid="6" /]
[/collapse]
[collapse status="false" title="主板BIOS设置"]
[button color="warning" icon="" url="https://www.bilibili.com/video/BV1rJ411r7Jt/" type="round"]BIOS设置[/button] 
开机F2  
| :-----: | :-----: |
|Dell Inspiron 15-7579 Settings |

| :----- | :----- |:----- |:----- |
|System Configuration |SATA Operation|AHCI|硬盘模式
|System Configuration | Miscellaneous Devices  |Enable Secure Digital (SD)Card |关闭SD读卡器
|Secure Boot |Secure Boot Enable  |Disabled |关闭安全启动

开机按“F2”，进入到Bios界面，修改bios ：
1、Secure Boot - Secure Boot Enable里改成Disabled
2、General - Advanced Boot Options里，Enable Legacy Option ROMs勾上
3、System Configuration - SATA Operation 改成 AHCI
4、Boot Sequence - Boot List Option设置为UEFI

[button color="light" icon="" url="https://www.jianshu.com/p/e490108cd6e6" type="round"]BIOS[/button]

[/collapse]

  [1]: /usr/uploads/2021/05/1283761626.png
  [2]: /usr/uploads/2021/05/2658837323.png
  [3]: /usr/uploads/2021/05/3760063740.png
  [4]: /usr/uploads/2021/05/1229535391.png
  [5]: /usr/uploads/2021/05/2095622664.png
  [6]: /usr/uploads/2021/05/1470531843.png
  [7]: /usr/uploads/2021/05/234098892.png
  [8]: /usr/uploads/2021/05/1328430533.png
  [9]: /usr/uploads/2021/05/2337780209.png
  [10]: /usr/uploads/2021/05/2231663261.png
  [11]: /usr/uploads/2021/05/2666002745.png
