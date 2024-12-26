# macOS on RedmiBook Pro 15S
## 配置

Type | Spec
:---------|:---------
Model Name | RedmiBook Pro 15S 2021
CPU | AMD Ryzen™ 7 5800H
RAM | 16 GB 3200 MHz DDR4
Wi-Fi | Intel® Wi-Fi 6 AX200
Audio | Realtek ALC256

## 安装时需要关闭的驱动

驱动 | 
:---------|
AirportItlwm |
IntelBluetoothFirmware |
IntelBluetoothInjector | 
IntelBTPatcher | 
BlueToolFixup | 
NootedRed | 

> 当系统完全安装完毕时（系统激活完毕）将以上关闭驱动再次打开，如果你是5600H只需要修改AMD内核补丁即可。当前`OpenCore 1.0.2`


## 睡眠问题
通过ACPI补丁可以开启S3睡眠，但是会有些问题（睡眠唤醒后合盖无法息屏），当前问题尚未能解决，如果改问题解决请联系我。


ACPI文件 | 作用
:---------|:---------
SSDT-BATT-fix.aml | 修复电池循环(若要使用睡眠功能，不建议打开此补丁)
SSDT-BTIF.aml | 开启S3睡眠并修复电池状态显示

> 这两个同时开启，电池百分比会用一段时间突然显示低电量（5%）实际上充电口是绿灯



## 白果网卡
目前仅测试过两块白果网卡`BCM94360CS2`、`BCM94360Z4`这两块网卡蓝牙正常， WI-FI无法使用。在windows中网卡是正常使用，Hackintool能够识别PCIE地址但是无法使用Wi-Fi

## 内置麦克风
1. Set csr-active-config to 01000000.
2. [Download](https://github.com/qhuyduong/AMDMicrophone/releases/latest) the kext from Github Actions.
3. Copy it to /Library/Extensions/.

```shell
sudo cp -r AMDMicrophone.kext /Library/Extensions/
```

## 感谢
`Lynx`、[维奇](https://github.com/weachy) 提供的帮助