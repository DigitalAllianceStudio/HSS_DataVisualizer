<table style = "width: 100%;">
<tr>
<td colspan="2">

:beers: HSS_DataVisualizer & UNI_DataVisualizer <a title="Hits" target="_blank" href="https://github.com/DigitalAllianceStudio/HSS_DataVisualizer"><img src="https://hits.b3log.org/DigitalAllianceStudio/HSS_DataVisualizer.svg"></a>

![专业版03](doc/专业版03.png)
![专业版04](doc/专业版04.png)

> [!NOTE]
> 本仓库用于 HSS_DataVisualizer & UNI_DataVisualizer 的发布， 当前版本: **v1.0.0.0**，下载请跳转程序发布页面 [github](https://github.com/DigitalAllianceStudio/HSS_DataVisualizer/releases/latest) 或 [gitee](https://gitee.com/tomystark/DataVisualizer-Release/releases/latest)

> [!NOTE]
> RTT 模式下，目标 MCU 端 RTT 库的移植和使用请参考该工程：[https://github.com/SummerFalls/F031K6T6_TestProj](https://github.com/SummerFalls/F031K6T6_TestProj)
>
> 其它参考资料：
> 1. [RTT: Instrumenting an application to use it with J-Scope](https://kb.segger.com/UM08028_J-Scope#RTT:_Instrumenting_an_application_to_use_it_with_J-Scope)
> 2. [SEGGER's Real Time Transfer (RTT)](https://kb.segger.com/RTT)

> [!TIP]
> :question: 使用 Texas Instruments 的芯片（例如 `TMS320F28035` 以及国产1:1替代芯片例如湖南进芯的DSP，例如 `ADP32F035`，以及 `MSP430` 等...）和 `XDS100v3`、`XDS110`、`XDS560v2 Plus` 等调试器？
>
> :bulb: 请使用适用于 Texas Instruments 德州仪器芯片的非侵入式数据可视化实时示波工具：`DSS_DataVisualizer`，仓库地址：[https://github.com/DigitalAllianceStudio/DSS_DataVisualizer](https://github.com/DigitalAllianceStudio/DSS_DataVisualizer)

<!-- ![GIF1](doc/GIF1.gif) -->

</td>
</tr>
<tr>
<td style = "width: 30%;">

![ProgramScreenshot10](doc/ProgramScreenshot10.png)
![ProgramScreenshot7](doc/ProgramScreenshot7.png)

## :book: 简介

本工具套件发布包内涵 2 个工具：`HSS_DataVisualizer` 和 `UNI_DataVisualizer`，均支持 High-Speed-Sampling (HSS) 和 Real-Time-Transfer (RTT) 模式，通过 SWD/JTAG 接口，对 MCU RAM 中的全局变量进行非侵入式的后台高速访问，并实时将波形和数据可视化到用户界面，其原理类似于 J-Scope、STM Studio、STM32CubeMonitor。

</td>
<td style = "width: 70%;">

![ProgramScreenshot8](doc/ProgramScreenshot8.png)

> [!TIP]
> 本工具是 J-Scope 的完美平替，相比 J-Scope，本工具支持和新增的功能：

1. 变量别名设定
2. 变量`公式计算`实时显示（支持 `Javascript Math` 表达式、移位等操作）
3. 更便利的变量地址重新解析功能（支持 AXF/ELF/OUT 等格式）
4. 新增观测的同时`修改变量的功能`
5. 更棒的变量增删改查、采样使能、波形使能体验
6. 更便利和高清的示波图操作（模式有`扫描模式`、`滚动模式`：支持滚动、缩放、平移、游标测量等操作）
7. 支持 2D 示波图、3D 示波图、3D 图形
8. 支持`采样数据导出 CSV`
9. 以附加模式连接（不复位芯片）

</td>
</tr>
<tr>
<td colspan="2">

> [!IMPORTANT]
> **注意事项：** :warning: 若运行报错（如`缺少动态链接库`），请安装 :package: `vcredist_x64.exe` 和 :package: `vc_redist.x64.exe` 运行库。

> [!NOTE]
> 本工具套件分为 4 个可执行程序：
> 1. HSS_DataVisualizer Std/Pro - SEGGER **J-Link** / **J-Trace** 专用数据可视化工具
> 2. UNI_DataVisualizer Std/Pro - 通用数据可视化工具（支持 **DAP-Link** / **ST-Link V2** （固件版本 `v2.26` 及以上） / **ST-Link V3** （固件版本 `v3.2` 及以上） / **J-Link** / **Black Magic** / **FTDI** / **WCH-Link** / **CH347usbjtag** / **Glasgow Interface Explorer** 等调试器...）

## 特性对比

| 特性 | HSS_DataVisualizer Std | HSS_DataVisualizer Pro | UNI_DataVisualizer Std | UNI_DataVisualizer Pro |
| --- | --- | --- | --- | --- |
| 调试器支持 | J-Link / J-Trace 专版优化（`J-Trace Cortex-M PRO V2` RTT 模式最高采样率测试可达 `1.94 MB/s`：单帧10个变量无时间戳合计29字节，每秒采样 `70K` 次） | J-Link / J-Trace 专版优化（`J-Trace Cortex-M PRO V2` RTT 模式最高采样率测试可达 `1.94 MB/s`：单帧10个变量无时间戳合计29字节，每秒采样 `70K` 次） | DAP-Link / ST-Link V2/V3 / J-Link / Black Magic / FTDI / WCH-Link / CH347usbjtag / Glasgow 等 | DAP-Link / ST-Link V2/V3 / J-Link / Black Magic / FTDI / WCH-Link / CH347usbjtag / Glasgow 等 |
| 采样模式 | HSS / RTT | HSS / RTT | HSS / RTT | HSS / RTT |
| CSV 采样数据导出 - 实时落盘 | ✅ | ✅ | ✅ | ✅ |
| CSV 采样数据导出 - 自定义导出路径 | ❌ （仅支持默认导出到桌面的 “采样数据导出” 文件夹） | ✅ | ❌ （仅支持默认导出到桌面的 “采样数据导出” 文件夹） | ✅ |
| CSV 采样数据导出 - 自定义文件分割、编号 | ❌ （单次启用仅支持单文件导出） | ✅ （可自定义每多少行采样数据自动分割一次文件） | ❌ （单次启用仅支持单文件导出） | ✅ （可自定义每多少行采样数据自动分割一次文件） |
| HSS 模式连接时自动重新解析变量 | ❌ | ✅ | ❌ | ✅ |
| RTT 模式丢包特殊处理* | ✅ | ✅ | ✅ | ✅ |
| 变量快捷搜索筛选 | ✅ | ✅ | ✅ | ✅ |
| 变量在线修改 | ✅ | ✅ | ✅ | ✅ |
| 独立的采样使能 | ✅ | ✅ | ✅ | ✅ |
| 独立的波形使能 | ✅ | ✅ | ✅ | ✅ |
| 变量别名 | ✅ | ✅ | ✅ | ✅ |
| 变量公式计算（支持 Javascript Math 表达式） | ✅ | ✅ | ✅ | ✅ |
| 最小值、最大值、滑动平均值 | ✅ | ✅ | ✅ | ✅ |
| 2D 示波图 - 单图模式 | ✅ | ✅ | ✅ | ✅ |
| 2D 示波图 - 多图模式 | ✅ | ✅ | ✅ | ✅ |
| 2D 示波图 - 单 / 多图模式 - X/Y 游标测量 | ✅ | ✅ | ✅ | ✅ |
| 2D 示波图 - 单 / 多图模式 - 滚动模式 | ✅ | ✅ | ✅ | ✅ |
| 2D 示波图 - 单 / 多图模式 - 扫描模式 | ✅ | ✅ | ✅ | ✅ |
| 3D 示波图 | ✅ | ✅ | ✅ | ✅ |
| 3D 图形 | ✅ | ✅ | ✅ | ✅ |
| 示波器主题切换 | ✅ | ✅ | ✅ | ✅ |
| Ribbon Style | ❌ | ✅ | ❌ | ✅ |
| 高级窗体停靠系统 | ❌ | ✅ | ❌ | ✅ |

> [!IMPORTANT]
> **HSS_DataVisualizer 注意事项：**

- 本工具仅支持 SEGGER **J-Link** / **J-Trace** 调试器（建议使用 `SEGGER` 官方驱动以获得更好的性能），使用其他调试器请使用通用数据可视化工具 `UNI_DataVisualizer`
- 较老版本的 J-Link 驱动安装路径问题
  > ![JLinkInstallPathNote](doc/JLinkInstallPathNote.png)
  > J-Link 驱动安装时的路径请不要带版本号，否则可能会导致程序无法正常工作，详细说明如上图所示。

> [!IMPORTANT]
> **UNI_DataVisualizer 注意事项：**

- **ST-Link V2/V3**：请确保已安装最新版的 ST-Link [固件 STSW-LINK007](https://www.st.com/en/development-tools/stsw-link007.html) 和 [驱动 STSW-LINK009](https://www.st.com/en/development-tools/stsw-link009.html)
- **J-Link**：需要通过 J-Link 官方软件包内的 `JLinkConfig.exe` 将 J-Link 配置为 WinUSB 驱动（某些 J-Link 在配置对话框中可能无法选择 WinUSB 选项，在这种情况下，请使用 [Zadig](https://zadig.akeo.ie/) 安装通用的 WinUSB 驱动程序），**若使用专用数据可视化工具 `HSS_DataVisualizer`，则建议使用 `SEGGER` 官方驱动以获得更好的性能，在通用数据可视化工具 `UNI_DataVisualizer` 中使用 J-Link 时才需要配置为 WinUSB 驱动** :warning: 注意：不建议在 `UNI_DataVisualizer` 中使用 J-Link，因为那样无法发挥 J-Link 的最强性能，实测 J-Link Ultra+ 在 `UNI_DataVisualizer` 中的采样速率只有 **500 次/秒**，而在 `HSS_DataVisualizer` 中则可高达 **33000 次/秒** ![JLinkConfigWinUSB](doc/JLinkConfigWinUSB.png)
- **Black Magic**：请参阅 [Black Magic 调试器官网](https://black-magic.org/index.html)、[Black Magic 调试器仓库](https://github.com/blackmagic-debug/blackmagic) 了解更多信息
- **FTDI**：FTDI 指的是使用 FTDI 公司的 USB-JTAG 桥接器构建的一系列调试器，`UNI_DataVisualizer` 支持使用了以下芯片的 FTDI 调试器（不支持 FTDI 官方的 VCP 或 D2xx 驱动，请使用 [Zadig](https://zadig.akeo.ie/) 安装通用的 WinUSB 驱动程序）：`FT232H`、`FT2232C`、`FT2232D`、`FT2232H`、`FT4232H`，例如 Olimex ARM-USB 系列调试器：`OLIMEX-ARM-USB-TINY-H`、`OLIMEX-ARM-USB-TINY`、`OLIMEX-ARM-USB-OCD-H`、`OLIMEX-ARM-USB-OCD`
- **WCH-Link**：请参阅 [WCH-Link 调试器官网](https://www.wch.cn/products/WCH-Link.html)、[WCH-Link 调试器仓库](https://github.com/ch32-rs/wlink)、[WCH-Link 调试器仓库参考文献](https://github.com/ch32-rs/wlink/blob/main/docs/references.md) 了解更多信息
- **CH347usbjtag**：请参阅 [CH347usbjtag 调试器官网](https://www.wch.cn/products/CH347.html)、[CH347usbjtag 调试器仓库](https://github.com/WCHSoftGroup/ch347) 了解更多信息
- **Glasgow Interface Explorer**：使用方法请参阅 [probe-setup 的 Glasgow Interface Explorer 章节](https://probe.rs/docs/getting-started/probe-setup/)，其它请参阅 [Glasgow Interface Explorer 调试器官网](https://glasgow-embedded.org/)、[Glasgow Interface Explorer 调试器仓库](https://github.com/GlasgowEmbedded/glasgow/) 了解更多信息

</td>
</tr>
</table>

## RTT 模式丢包特殊处理

RTT 模式下MCU 高频发包时，对于低端 JLink 的丢包情况进行了特殊处理（这个处理 JScope 竟然没有做，见下图），比如 JLink OB、JLink V9 等低端 JLink，让MCU直接在主循环按最高频率写RTT缓冲，会有很多封包出错（JLink OB 测试了下 RTT 极限速度好像就是在 134 KB/s 不过这个速度已经比较容易产生错误数据），所谓特殊处理，其实指的就是如果发生丢字节的情况，为了防止数据错乱，失去对齐导致采样值出现极大值、极小值的问题，目前的策略是将丢了字节的那一包整包丢弃，如下图所示，被丢弃的数据点会被填充为0。特殊处理前后对比如下：

### JScope 采样时发生丢包的波形界面截图

> 可以看到很多极大值、极小值充斥了整个波形界面

![JScope](doc/JScope.jpg)

### RTT丢包特殊处理前

![RTT丢包特殊处理前](doc/RTT丢包特殊处理前.png)

### RTT丢包特殊处理后

![RTT丢包特殊处理后](doc/RTT丢包特殊处理后.png)

<div align="center">

### 软件截图 - 专业版

![专业版01](doc/专业版01.png)
![专业版02](doc/专业版02.png)

### 软件截图 - 标准版

![标准版01](doc/标准版01.png)
![标准版02](doc/标准版02.png)
![ProgramScreenshot10](doc/ProgramScreenshot10.png)
![ProgramScreenshot8](doc/ProgramScreenshot8.png)
![ProgramScreenshot1](doc/ProgramScreenshot1.png)
![ProgramScreenshot2](doc/ProgramScreenshot2.png)
![ProgramScreenshot3](doc/ProgramScreenshot3.png)

### 采样数据导出 CSV

![ProgramScreenshotCSV](doc/ProgramScreenshotCSV.png)

</div>

----------

:star: Copyright © 2023 - 2026 Digital Alliance Studio. All rights reserved.
