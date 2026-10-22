# 嵌入式作业

## 目录说明

- `00_Reference/`：课程资料、芯片手册与参考文档。
- `01_Function_Map/`：作业要求、流程图与实验记录。
- `02_Hardware/`：原理图、接线图与硬件说明。
- `03_Firmware/`：经过验证、手动归档的发布固件。
- `04_Software/01_Source_Code/`：各作业的完整源码工程。
- `05_Tools/`：开发辅助工具与脚本。

空目录暂时使用 `.gitkeep` 占位，加入实际内容后可以移除该占位文件。

## 作业列表

| 作业 | 芯片 | 源码工程 |
| --- | --- | --- |
| 01LED | STM32F411CEU6 | [01LED](04_Software/01_Source_Code/01LED/) |

## 打开工程

- STM32CubeMX：[LED.ioc](04_Software/01_Source_Code/01LED/LED.ioc)。
- Keil MDK：[LED.uvprojx](04_Software/01_Source_Code/01LED/MDK-ARM/LED.uvprojx)。

现有配置使用 STM32Cube FW_F4 V1.27.1，目标工具链为 MDK-ARM V5；Keil 工程选择 ARM Compiler 5。请在本机安装对应工具、编译器与设备支持包。

使用 Keil 打开工程后，执行 Rebuild 检查编译结果。需要调整引脚或时钟时，在 CubeMX 中打开 `.ioc`；重新生成代码前先检查并保存自定义代码。

## 源码与固件管理

- 每项作业保持独立的完整工程；保留 `.ioc`、`Core/`、`Drivers/`、`MDK-ARM/` 以及工程所需的 RTE 和调试配置。
- 新作业放到 `04_Software/01_Source_Code/` 下，与 `01LED/` 并排存放。
- 日常编译产物、调试日志和个人界面状态不提交；当前 LED 工程的输出目录是 `MDK-ARM/LED/`。
- 新增工程时，按其实际输出目录补充 `.gitignore`，不要忽略整个 `MDK-ARM/`。
- 需要归档固件时，将经过验证的 `.hex` / `.bin` 手动复制到 `03_Firmware/<作业名>/<版本>/`，同时记录对应源码提交、用途和验证结果。
