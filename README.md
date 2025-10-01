# :beers: HSS Data Visualizer

## :book: 简介

本仓库用于 HSS Data Visualizer 的发布，下载请跳转 [发布页面 (当前版本: v0.0.1.3)](https://github.com/DigitalAllianceStudio/HSS_DataVisualizer/releases)

本程序通过 SEGGER High-Speed-Sampling (HSS) 方式，对 MCU 上的 RAM、Flash、寄存器进行非侵入式的后台高速访问，并实时可视化显示到用户界面，其原理类似于 J-Scope、STM Studio、STM32CubeMonitor。

在 J-Scope 的基础上，除了高速采样，额外增加了变量修改功能。

<div align="center">

![GIF1](doc/GIF1.gif)
![GIF2](doc/GIF2.gif)
![ProgramScreenshot1](doc/ProgramScreenshot1.png)
![ProgramScreenshot2](doc/ProgramScreenshot2.png)
![ProgramScreenshot3](doc/ProgramScreenshot3.png)
![ProgramScreenshot4](doc/ProgramScreenshot4.png)
![ProgramScreenshot5](doc/ProgramScreenshot5.png)

### 采样数据导出 CSV

![ProgramScreenshot6](doc/ProgramScreenshot6.png)

</div>

## :warning: 注意

- 若运行报错（如`缺少动态链接库`），请安装 `vcredist_x64.exe` 和 `vc_redist.x64.exe` 运行库。

----------

:star: Copyright © 2023 Digital Alliance Studio. All rights reserved.
