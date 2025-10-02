---
id: Board
aliases: []
tags:
  - Circuit
---

# Concepts
- [ ] 
| Term        | Description                                                                                                                                                                                                                                                               |
|-------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Bank**    | 一组共享相同供电电压和I/O标准的I/O引脚(IOB)。不同Bank可以配置为不同的电压标准，以支持多种外部接口。                                                                                                                                           |
| **QSPI**    | Quad Serial Peripheral Interface，高速串行接口，通常用于连接外部闪存(如配置FPGA的启动映像). 通过同时使用四条数据线实现比标准SPI更高的吞吐量。                                                                                                          |
| **DPAUX**   | DisplayPort Auxiliary Channel的缩写，是DisplayPort接口中的一个辅助通道。它用于传输链路管理、设备控制、中断请求和VESA EDID(扩展显示识别数据)等信息，不传输主视频/音频数据。                                                                                             |
| **ULPI**    | UTMI+ Low Pin Interface的缩写，是USB Transceiver Macrocell Interface Plus (UTMI+)的简化版本，用于连接USB主控制器和USB收发器(PHY)。ULPI接口减少了所需的引脚数量，从而降低了PCB复杂度和成本，常用于嵌入式USB应用。                                                               |
| **GTRs**    | Gigabit Transceivers的缩写，指的是FPGA内部集成的多千兆位收发器。它们是高速串行通信的核心组件，支持如PCIe、SATA、Ethernet、DisplayPort等多种高速协议，能够进行串行化和解串行化数据。                                                                                     |
| **SATA**    | Serial Advanced Technology Attachment的缩写，是一种计算机总线接口，用于连接主机适配器和硬盘驱动器、固态驱动器等大容量存储设备。在FPGA中，如果需要连接SATA设备，通常会通过GTRs实现SATA协议。                                                                                  |
| **Form Factor** | 指的是电子设备的物理尺寸、形状和布局。在电路板设计中，Form Factor决定了板子的大小、安装孔的位置、连接器的布局等，例如ATX、Micro-ATX是常见的PC主板Form Factor。FPGA芯片本身也有不同的封装Form Factor。                                                               |
| **LA Bus**  | 通常指Logic Analyzer Bus，即逻辑分析仪总线。它是一组FPGA内部或连接到FPGA的信号线，用于调试目的。这些信号可以被外部逻辑分析仪捕获，以监控FPGA内部信号的时序和状态，或者在某些情况下，也可以指FPGA内部的通用逻辑互连总线。                                                                 |
