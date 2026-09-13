# Breadboard to FPGA 8-bit CPU 项目规划

> 从 74LS 系列芯片的面包板计算机出发，经过 Logisim 仿真和 Verilog 重构，最终部署到 Sipeed Tang Nano 9K FPGA。

## 1. 项目定位

这是一个跨学期、低压力、可持续推进的计算机体系结构实践项目。它不是为了尽快照着教程接完所有线，而是要用四种不同的表达方式理解同一台 8 位计算机：

1. 面包板和 TTL 芯片：看见真实电信号、总线、时钟和控制线。
2. Logisim：把电路抽象成清晰的数字逻辑模块。
3. Verilog：把结构和时序准确地描述成硬件。
4. Tang Nano 9K FPGA：完成综合、约束、下载和板上验证。

最终项目名称暂定为：

**Breadboard to FPGA 8-bit CPU**

建议未来 GitHub 仓库名：

```text
breadboard-to-fpga-8bit-cpu
```

仓库前期保持 Private，达到公开标准后再改为 Public。仓库名称、描述和可见性以后都可以修改。

## 2. 最终成果

项目完成时，至少应当具备以下成果：

- 一台能够逐步运行和自动运行的面包板 8 位计算机。
- 一套与实体机行为一致的 Logisim 模型。
- 一套模块化 Verilog RTL 实现及测试平台。
- 在 Tang Nano 9K 上运行的 FPGA 版本。
- 一个简单但清晰的演示程序，例如完成若干加减运算并输出结果。
- 完整的架构图、指令集、控制信号表、测试记录和调试日志。
- 一段可用于简历和 LinkedIn 的项目介绍。
- 图片或短视频，能够证明每个阶段确实运行过。

项目主线如下：

```mermaid
flowchart LR
    A[ECED 3204 基础] --> B[TTL 面包板计算机]
    B --> C[Logisim 数字逻辑模型]
    C --> D[Verilog RTL 与 Testbench]
    D --> E[Tang Nano 9K FPGA]
    E --> F[GitHub / LinkedIn / 简历]
```

## 3. 范围控制

### 3.1 MVP：必须完成

MVP 是可以公开展示的最低完整版本。具体位宽和存储容量以套件教程的实际设计为准。

- 稳定的时钟和复位。
- 8 位数据总线。
- A、B 或等价的通用数据寄存器。
- ALU，至少支持加法和减法。
- Carry 和 Zero 等必要状态标志。
- 程序计数器 PC。
- 指令寄存器 IR。
- RAM 或等价程序/数据存储结构。
- 输出寄存器和 LED 输出。
- 自动控制单元或微码控制单元。
- 一组可以运行简单程序的指令。
- 手动单步与自动运行模式。
- Logisim、Verilog 和 FPGA 三个版本的行为对照测试。

建议的基础指令集可以参考下表，但最终应以套件教程及自己的架构决定为准：

| 类别 | 示例指令 | 作用 |
| --- | --- | --- |
| 数据传送 | `LDA`、`LDI`、`STA` | 读取立即数、加载和存储数据 |
| 算术 | `ADD`、`SUB` | 完成基本计算 |
| 跳转 | `JMP`、`JC`、`JZ` | 顺序控制和条件分支 |
| 输出 | `OUT` | 将结果写入输出寄存器 |
| 控制 | `NOP`、`HLT` | 空操作和停止运行 |

### 3.2 Stretch Goals：完成 MVP 后再选

以下内容都很酷，但任何一项都不应阻碍 MVP 完成：

- 更多逻辑运算：AND、OR、XOR、移位。
- 增加寄存器或扩展寻址空间。
- 增加 stack、subroutine 或更完整的条件分支。
- 编写一个小型 assembler。
- UART 输出和调试监视器。
- 数码管、SPI LCD 或 HDMI 输出。
- 在 FPGA 版本上加入更高频率时钟。
- 对比微码控制和硬连线控制。
- 设计第二版 ISA，记录兼容性变化。

规则：任意时刻只允许一个 Stretch Goal 处于进行中。

## 4. 硬件与软件

### 4.1 已选硬件

- 74LS 系列 8 位计算机套件。
- 面包板、跳线、杜邦线、LED、按钮和电阻。
- NE555 时钟相关器件。
- AT28C16 EEPROM。
- Arduino Nano，可用于 EEPROM 编程或辅助测试。
- Sipeed Tang Nano 9K，核心器件为 GW1NR-9 FPGA。

### 4.2 软件建议

- 电路仿真：Logisim-evolution。
- HDL：Verilog-2001 或项目工具链稳定支持的 Verilog 子集。
- FPGA 工具：Gowin EDA 及 Tang Nano 9K 官方下载工具。
- HDL 编辑：VS Code。
- 仿真：先选 Icarus Verilog 或 Verilator 中的一种，避免同时维护两套流程。
- 版本控制：Git 和 GitHub Private repository。
- 图表：Mermaid、draw.io 或清晰的手绘图扫描件。

### 4.3 电脑分工

- Windows：Gowin EDA、开发板下载、驱动、串口及 ECED 3204 实验的主要环境。
- Mac：资料阅读、Git、文档、Logisim、Verilog 编辑和可用的软件仿真。
- 重要原则：项目文件全部进入 Git，避免被某一台电脑绑定。

## 5. 学期时间线

时间线按照当前课程优先、工作日繁忙、周末集中推进来设计。日期可以随着套件到货时间整体平移。

### 阶段 0：课程基础与项目准备

**建议时间：2026 年 9 月至 12 月**

目标：不与 ECED 3204 抢时间，先建立理解和项目基础。

任务：

- 建立 Private GitHub 仓库。
- 保存套件清单、教程链接、FPGA 官方资料和芯片 datasheet。
- 理解二进制、补码、寄存器、ALU、PC、RAM、总线和控制信号。
- 将 AVR 汇编中的寄存器、标志位、跳转和内存访问概念映射到 CPU 结构。
- 安装并验证 Logisim-evolution。
- 安装 Git、VS Code 和基础 Verilog 工具。
- 期末高压期允许完全暂停。

完成标准：

- 能用自己的话说明一条指令从 fetch 到 execute 发生了什么。
- 能解释寄存器、ALU、PC、IR、RAM 和控制单元的作用。
- Repo 已存在，资料来源已记录，项目范围已锁定。

### 阶段 1：TTL 面包板计算机

**建议时间：套件到货后，约 8 至 12 个周末**

不要一次搭完整机。每个模块都要经历“理解、搭建、测试、记录”四步。

| 里程碑 | 模块 | 主要验证 |
| --- | --- | --- |
| M1 | 电源、时钟、复位 | 单步稳定、自动时钟可调、复位可重复 |
| M2 | 数据总线与输出 | 只有一个模块驱动总线，LED 结果正确 |
| M3 | 寄存器 | load、enable、hold 行为正确 |
| M4 | ALU 与 flags | 加减法、Carry、Zero 边界测试正确 |
| M5 | Program Counter | count、jump、reset 正确 |
| M6 | RAM 与 Instruction Register | 地址、读写和指令锁存正确 |
| M7 | Control Unit | 每个 microstep 的控制字正确 |
| M8 | 全机集成 | 可运行第一个完整程序 |

每完成一个模块，必须留下：

- 一张接线清晰的照片。
- 一张模块方框图或原理说明。
- 输入、预期输出、实际输出的测试表。
- 至少一条调试记录。
- 一次 Git commit。

面包板阶段的硬件纪律：

- 插入芯片前先确认电源电压和极性。
- 所有模块必须共地。
- 每颗芯片附近配置合适的去耦电容。
- TTL 输入不要悬空。
- LED 必须使用限流电阻。
- 调试时优先使用低速手动时钟。
- 总线冲突、按钮抖动、接触不良和电源噪声应首先排查。
- FPGA 与 5 V TTL 不直接连接；若以后需要互联，先确认双方 I/O 电压并设计电平转换。

阶段演示程序建议：

```text
加载 7
加 5
减 3
输出 9
停止
```

完成标准：

- 冷启动后可以重复运行同一程序。
- 手动单步时能够逐个解释总线值和控制信号。
- 自动运行时结果稳定，而不是偶然成功一次。

### 阶段 2：Logisim 重建

**建议时间：3 至 5 个周末**

目标：在没有接触不良和电源噪声的环境中，验证架构逻辑本身。

任务：

- 先创建寄存器、ALU、PC、RAM、IR 和 control unit 子电路。
- 再用统一的 8 位总线连接模块。
- 标注所有信号名称和位宽。
- 创建单步时钟和复位输入。
- 使用与面包板相同的测试程序。
- 对照记录每个 microstep 的 PC、IR、flags、bus 和 register 值。

完成标准：

- Logisim 与面包板执行相同程序并得到相同结果。
- 至少覆盖加法进位、减法、Zero flag、jump 和 halt。
- 架构图足够清晰，陌生人可以找到 datapath 和 control path。

### 阶段 3：Verilog RTL

**建议时间：6 至 10 个周末**

目标：从“画电路”转向“准确描述同步硬件”。

推荐模块顺序：

1. `clock_divider`，仅用于板上低速观察。
2. `register_8bit`。
3. `alu_8bit`。
4. `program_counter`。
5. `instruction_register`。
6. `ram` 或初始化 ROM。
7. `control_unit`。
8. `cpu_core`。
9. `top_tang_nano_9k`。

每个模块都必须先写 testbench，再进入整机集成。最低测试集合：

| 模块 | 最低测试 |
| --- | --- |
| Register | reset、load、hold、output enable |
| ALU | 0、1、最大值、进位、借位、结果为零 |
| PC | reset、increment、jump、保持 |
| RAM/ROM | 地址边界、读写或初始化内容 |
| Control Unit | 每条指令的每个 microstep |
| CPU Core | 完整程序、条件跳转、halt |

Verilog 编码规则：

- 时序逻辑使用非阻塞赋值 `<=`。
- 组合逻辑使用阻塞赋值 `=` 并提供完整默认值。
- 明确 reset 是同步还是异步，并在所有模块中保持一致。
- 不依赖仿真才成立、综合后消失的写法。
- 不通过人为延时模拟真实硬件行为。
- 所有警告都要阅读，不能只看“综合成功”。
- CPU core 与开发板 top module 分离，避免板卡引脚污染核心设计。

完成标准：

- 所有模块 testbench 通过。
- CPU testbench 自动检查最终输出，而不是只靠人工看波形。
- RTL 与 Logisim 对同一程序给出一致结果。
- 无意外 latch、多个驱动或未约束时钟。

### 阶段 4：Tang Nano 9K 部署

**建议时间：3 至 6 个周末**

目标：完成从 RTL 到真实 FPGA 的全流程。

任务顺序：

1. 先跑官方 LED blink 示例，确认驱动、线缆、下载器和约束文件。
2. 用按键控制计数器，验证输入、消抖和复位。
3. 部署独立 ALU 或寄存器测试工程。
4. 接入完整 CPU core。
5. 用板载 LED 显示输出和调试状态。
6. 检查综合报告、资源使用和时序报告。
7. 保存最终 bitstream 生成步骤，不只保存生成文件。

完成标准：

- 断电重启后可以重新部署并复现结果。
- 板上程序与 Logisim、RTL 仿真结果一致。
- pin constraints、时钟频率和 reset 逻辑有文档。
- 有一段清晰的视频显示 reset、run、output 和 halt。

### 阶段 5：整理与公开

**建议时间：1 至 2 个周末**

任务：

- 整理 README 首页。
- 删除密钥、个人路径、临时文件和不必要的生成文件。
- 添加开源许可证，确认引用和教程署名。
- 将关键照片压缩后放入 repo。
- 制作 60 至 90 秒演示视频。
- 将仓库改为 Public。
- 添加 LinkedIn Project，并链接 GitHub。
- 将项目压缩成简历中的 2 至 3 条 bullet points。

## 6. 每周时间安排

### 正常教学周：每周约 3 小时

| 时间 | 时长 | 内容 |
| --- | ---: | --- |
| 工作日任选一天 | 15 至 25 分钟 | 看一小段教程、读 datasheet、整理疑问或补项目日志 |
| 周六或周日 | 2 至 3 小时 | 唯一的深度工作块：搭建、测量、仿真或写 Verilog |
| 深度工作结束前 | 15 至 20 分钟 | 拍照、记录结果、commit、写下下一步 |

工作日不安排必须完成的硬件任务。当天课程重或精神状态差时，可以完全跳过。

### 考试周：每周 0 至 20 分钟

- 不搭新模块。
- 不做大范围重构。
- 只记录突然想到的问题或整理已有照片。
- 课程优先，暂停项目不算落后。

### 假期或 Reading Week：每周 4 至 6 小时上限

- 最多安排两个深度工作块。
- 每次只处理一个模块。
- 不用一次性“补回”之前暂停的时间。

### 单次深度工作模板

```text
10 分钟：查看上次日志，确认今天唯一目标
20 分钟：阅读原理图、真值表或教程
70 分钟：搭建或编码
30 分钟：测试与定位问题
20 分钟：记录、拍照、提交 Git
10 分钟：写下下一次最小动作
```

若 30 分钟内没有任何进展，停止继续随机改线，转为记录信号、测电压、画连接图或缩小测试范围。

## 7. Repo 结构

建议最终结构：

```text
breadboard-to-fpga-8bit-cpu/
├── README.md
├── PROJECT_PLAN.md
├── LICENSE
├── docs/
│   ├── architecture.md
│   ├── instruction-set.md
│   ├── control-signals.md
│   ├── test-plan.md
│   ├── project-log.md
│   └── references.md
├── breadboard/
│   ├── diagrams/
│   ├── tests/
│   └── photos/
├── logisim/
│   ├── cpu.circ
│   └── test-programs/
├── verilog/
│   ├── rtl/
│   ├── tb/
│   ├── programs/
│   └── scripts/
├── fpga/
│   ├── tang-nano-9k/
│   └── constraints/
├── media/
│   ├── images/
│   └── demo/
└── .gitignore
```

不要在第一天创建所有空文件。某一阶段真正开始时再建立对应目录。

## 8. Git 工作方式

### 分支

个人项目早期只使用 `main` 即可。需要尝试高风险改动时，再创建短期 feature branch。

### Commit 规则

一次 commit 只表达一个可说明的变化，例如：

```text
docs: define initial CPU architecture
breadboard: verify clock module at three speeds
logisim: add 8-bit register subcircuit
rtl: implement ALU add and subtract operations
test: cover carry and zero flags
fpga: map CPU output to onboard LEDs
```

不要使用只有 `update`、`stuff` 或 `fix` 的 commit message。

### Issue 规则

把问题写成可验证的小任务：

```text
Bad: Build the CPU
Good: Verify register A loads bus value on the rising clock edge
```

同时只保持一个主要 issue 为 In Progress。

## 9. 文档与证据

每个阶段都应回答四个问题：

1. 这个模块要解决什么问题？
2. 它的输入、输出和状态是什么？
3. 我如何证明它工作正确？
4. 我遇到了什么错误，最后如何定位？

### 最小项目日志模板

```markdown
## YYYY-MM-DD - 模块名称

Goal:

What I changed:

Test performed:

Expected result:

Actual result:

Problem and diagnosis:

Next smallest step:
```

### 测试证据优先级

1. 自动化 testbench 及输出。
2. 明确输入和输出的测试表。
3. 波形截图或逻辑分析结果。
4. 面包板照片和演示视频。
5. 单纯描述“它能运行”。

## 10. AI 协作原则

AI 可以显著减少 paperwork，但不能替代你对硬件行为的理解。

适合交给 AI 的内容：

- 将零散实验笔记整理成 `project-log.md`。
- 根据真实架构生成 README 初稿。
- 整理 instruction table、control signal table 和测试矩阵。
- 解释 datasheet、Verilog 报错和仿真波形。
- 生成 testbench 初稿及边界测试建议。
- 检查文档是否前后一致。
- 将项目改写成 LinkedIn 和简历语言。
- 帮助把一个大任务拆成下一次 30 分钟能完成的小任务。

必须由自己提供或验证的内容：

- 真实接线和引脚映射。
- 实际测量值、测试结果和故障现象。
- 最终 ISA 和控制时序的设计决定。
- 代码是否能综合、下载和在板上运行。
- 照片、视频、波形和演示结果。
- 对引用教程和开源代码的署名。

推荐协作流程：

```text
你提供：本周做了什么、哪里失败、怎么测试、最终结果
AI 负责：整理文档、提出检查项、补充测试、润色表达
你确认：所有技术事实与实际硬件一致
```

提交任何课程作业前，应遵守课程的学术诚信和 AI 使用规则。这个个人项目可以广泛使用 AI 辅助，但公开时应能亲自解释每个核心模块。

## 11. 风险与应对

| 风险 | 典型表现 | 应对 |
| --- | --- | --- |
| 时间不足 | 两周没有推进后产生负罪感 | 使用最小模式，考试周直接暂停 |
| 范围膨胀 | MVP 未完成就做 HDMI、RISC-V | 将想法放入 Backlog，先完成 OUT + HLT |
| 面包板不稳定 | 时好时坏、换速度就失败 | 降低时钟、检查电源、共地、悬空输入和总线冲突 |
| 只会照教程 | 拔掉教程就不知道下一步 | 每个模块先写自己的输入、输出、真值表和测试 |
| 仿真正确但 FPGA 错误 | 板上无输出或随机行为 | 检查 pin、时钟、reset、约束、同步输入和综合警告 |
| AI 生成内容不可靠 | 文档漂亮但与实物不符 | 所有结果附测试证据，技术事实由本人确认 |
| Git 仓库混乱 | 大量生成文件和无意义 commits | 使用 `.gitignore`，按模块小步提交 |
| 硬件损坏 | 芯片过热、输出冲突 | 断电改线，先测电源，不直连电压标准不明的接口 |

## 12. 完成定义

项目不是以“所有可能功能都做完”为结束，而是满足以下条件时宣布 v1.0：

- 面包板、Logisim、Verilog 仿真和 FPGA 四个版本都能运行同一个演示程序。
- 四个版本的最终输出一致。
- 核心模块和指令集有文档。
- Verilog 有自动化测试。
- FPGA 工程可以从干净环境重新构建。
- README 中有架构图、运行方法、测试结果和演示媒体。
- 所有引用和借鉴内容均有来源说明。
- 你可以在 5 分钟内不看稿解释 datapath、control unit 和一条指令的执行过程。

## 13. Portfolio 发布文案草稿

### LinkedIn Project

**Breadboard to FPGA 8-bit CPU**

Built and verified an educational 8-bit computer across four implementation layers: TTL breadboard logic, Logisim simulation, Verilog RTL, and a Sipeed Tang Nano 9K FPGA. Implemented and documented the datapath, ALU, registers, program counter, memory interface, instruction decoding, control sequencing, and a small custom instruction set. Developed module-level tests and compared execution behavior across physical hardware, simulation, and FPGA deployment.

### Resume Bullets

- Built an 8-bit CPU from 74LS-series TTL logic and reproduced the architecture in Logisim and synthesizable Verilog.
- Designed and tested the ALU, registers, program counter, memory interface, instruction decoder, and control unit using module-level testbenches.
- Deployed the CPU to a Tang Nano 9K FPGA and documented cross-platform validation, hardware debugging, ISA behavior, and timing/control signals.

公开前应根据最终真实成果删改文案，未完成的功能不能提前写成已完成。

## 14. 当前下一步

现阶段只做以下三件事：

- [ ] 创建 GitHub Private repository：`breadboard-to-fpga-8bit-cpu`。
- [ ] 建立 `docs/references.md`，记录套件教程、芯片 datasheet 和 Tang Nano 9K 官方资料。
- [ ] 用一页自己的话解释 fetch、decode、execute，以及 PC、IR、ALU、RAM 的数据流。

在 ECED 3204 进行期间，不要求开始大规模接线。当前课程里每理解一个汇编指令、寄存器或状态标志，都可以把它映射回这台未来要亲手实现的 CPU。

## 15. 总原则

这个项目的价值不取决于完成速度，而取决于你是否能证明每一层都真正理解并验证过。

**一次只做一个模块；每个模块都测试；每次测试都记录；课程永远优先。**
