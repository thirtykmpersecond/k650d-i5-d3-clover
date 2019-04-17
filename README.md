# **k650di5d3**
## 这个EFI在10.13.6最新版基础上完善，完美程度99%还有1%没发现，一直单系统稳定使用几个月。当然也适用于10.14.4（个人建议使用10.13.6养老）。  
### 现在电脑各项功能正常：  
**声卡**：威盛VT1802，ID使用3，33都没问题。  
**有线网卡**：有线网卡使用RealtekRTL8111.kext。1.2.2版本，使用其他版本可能出现：已经插好网线提示，电缆已拔出的问题。  
**无线网卡**：自带ac3160无解，换bcm95352hmb，存在睡眠唤醒后wifi打不开情况的请自行去屏蔽针脚，好像是28针，记不太清楚了。可百度到案例。  
**蓝牙**：ac3160的蓝牙可以用，但是不能关闭，换了bcm94352hmb。  
**核心显卡**：hehd4600 ，ID使用0416000，发现在这台电脑上比0a260006好用，显存1024m通过补丁修改为2048.如果花屏请打开csm，我的目前没有打开csm也不花屏，但是有个小问题就是开机不出现logo，驱动显卡后才会出现logo'给人开机快的感觉，以前不存在这个问题可能是使用whatevergreen驱动亮度导致的，目前没去管他，因为单系统运行。这个不碍眼，甚至觉得更好。  
**独立显卡**GTX950m（无解，已经屏蔽。）。  
**睡眠**:ok，可以通过usb键盘，鼠标唤醒，本人呢换了网卡bcm94352hmb，也可以通过蓝牙唤醒。  
**休眠**：不会自动进入休眠状态，可通过快捷键FN+F12进去休眠模式。  
**亮度**：以前使用dsdt打补丁驱动亮度，在升级后存在打开csm和720p分辨率时开机亮度很暗，需要重新切换分辨率才会正常，，如果关闭csm能够解决，但是开机会有八个苹果，现在通过whatevergreen自带的驱动亮度方法，解决了这些问题，但是出现新问题，驱动显卡前不出logo，打开-v也不跑码。如果使用最大分辨率的建议只勾选ddpnlf，取消Devices下的SetintelBackight和SetintelmaxBackight。应该就会正常出现logo。（个人没试）  
**变频**：应该正常，生成了变频的ssdt文件，以前是9档变频，可通过cpufriend修改为六档，但是最近没去关注这些，因为在使用中温度正常。不插电能使用两个小时，电脑买了3年了，平时一直插电源使用，晚上宿舍断电后才使用电池。  
**HDMI**：hdmi正常，hdmi音频可以有输出但是音乐卡卡的，所以一直没使用。  
**USB**：USB一切正常。  
**DSDT**：这次分享的efi是从新修改过dsdt，以前小白的时候修改的dsdt，什么都不知道打了太多无用的补丁，现在的dsdt只做了usb端口定制，舍弃usbinjectall。和解决屏蔽独显和勾选addpnlf驱动亮度后，开机风扇狂转不停，高温报警的问题。（本人喜欢简洁所以没用hotpatched，只在一个dsdt上做修改）  
**开机鼠标卡顿的问题**：通过屏蔽hdmi，105端口解决开机卡顿问题,详见config（仅适用于10.13.6）。  
**本引导在10.13.6基础上修改，如果使用最新版14.3应该也没啥问题，如果有问题在讨论。
如果没换网卡，或者换了别的网卡的请删除EFI/clover/kexts/other下的：FakePCIID_Broadcom_WiFi.kext，AirportBrcmFixup.kext，BrcmFirmwareData.kext，BrcmPatchRAM2.kext这四个驱动。**  
