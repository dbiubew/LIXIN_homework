# 嵌入式作业

## 目录说明

- `00_Reference/`：课程资料、芯片数据手册与外部参考文档。
- `01_FunctionMap/`：作业要求、流程图，以及软硬件具体功能说明。
- `02_Hardware/`：项目自己的原理图、接线图与软硬件接口说明。
- `03_Firmware/`：运行在单片机上的完整固件工程；应用程序放在 `02_APP/`，需要 Bootloader 时再增加 `01_Bootloader/`。
- `04_Software/`：PC 及移动端配套软件，按需增加对应子目录。
- `05_Tools/`：开发过程中使用的构建、测试和辅助工具。

空目录暂时使用 `.gitkeep` 占位，加入实际内容后可以移除该占位文件。机械结构和工厂测试目录暂不创建；工具目录沿用已确定的 `05_Tools/` 编号。

## 作业列表

| 作业 | 芯片 | 固件工程 |
| --- | --- | --- |
| 01LED | STM32F411CEU6 | [01LED](03_Firmware/02_APP/01LED/) |

## 打开工程

- STM32CubeMX：[LED.ioc](03_Firmware/02_APP/01LED/LED.ioc)。
- Keil MDK：[LED.uvprojx](03_Firmware/02_APP/01LED/MDK-ARM/LED.uvprojx)。

现有配置使用 STM32Cube FW_F4 V1.27.1，目标工具链为 MDK-ARM V5；Keil 工程选择 ARM Compiler 5。请在本机安装对应工具、编译器与设备支持包。

使用 Keil 打开工程后，执行 Rebuild 检查编译结果。需要调整引脚或时钟时，在 CubeMX 中打开 `.ioc`；重新生成代码前先检查并保存自定义代码。

## 固件工程与版本管理

- 每项作业保持独立的完整工程；保留 `.ioc`、`Core/`、`Drivers/`、`MDK-ARM/` 以及工程所需的 RTE 和调试配置。
- 新的单片机应用工程放到 `03_Firmware/02_APP/` 下，与 `01LED/` 并排存放。
- 日常编译产物、调试日志和个人界面状态不提交；当前 LED 工程的输出目录是 `MDK-ARM/LED/`。
- 新增工程时，按其实际输出目录补充 `.gitignore`，不要忽略整个 `MDK-ARM/`，也不要笼统忽略所有 `.lib` 或 `.sct` 文件。
- 需要归档固件时，将经过验证的 `.hex` / `.bin` 手动复制到各工程的 `Release/<版本>/` 目录，例如 `03_Firmware/02_APP/01LED/Release/v1.0.0/`，同时记录对应源码提交、用途和验证结果；有实际发布内容时再创建该目录。
- `.gitignore` 只对 `03_Firmware/01_Bootloader/<工程名>/Release/` 和 `03_Firmware/02_APP/<工程名>/Release/` 下的归档 `.hex` / `.bin` 放行，避免日常编译固件混入版本管理。
