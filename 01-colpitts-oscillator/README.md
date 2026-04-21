# 01-Colpitts-Oscillator | 考毕兹振荡器：从仿真到实测

[![Janson Lab](https://img.shields.io/badge/Laboratory-JansonLab-blue?style=for-the-badge)](https://jansonlab.com)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)

> **Janson Lab 硬件系列第 01 期**：探索无线电技术的基石——LC 振荡器。

本项目详细记录了一个 2.8MHz 考毕兹振荡器的设计、仿真及硬件实现过程。

## 📺 关联视频
- **YouTube**: [点击观看：为什么它是最经典的振荡电路？](https://youtube.com/jansonlab)
- **Bilibili**: [点击观看：硬核拆解考毕兹振荡器](https://bilibili.com/...)

---

## 1. 项目简介 (Overview)
考毕兹振荡器（Colpitts Oscillator）通过电容分压器提供反馈，与电感组成 LC 谐振回路。本项目旨在验证其在 2MHz-3MHz 频段的稳定性和波形纯净度。

### 核心指标：
- **目标频率**: 2.8 MHz
- **实测频率**: 2.82 MHz (误差 < 1%)
- **输出波形**: 正弦波 (Sine Wave)
- **供电电压**: 9V DC

---

## 2. 仿真验证 (Simulation)
在动手焊接前，我们使用 **LTspice** 对电路进行了严谨的瞬态分析和 FFT 频谱分析。

### 仿真关键参数：
- **L**: 100µH (色环电感)
- **C1**: 100pF (NPO/C0G 瓷片电容)
- **C2**: 100pF (NPO/C0G 瓷片电容)

[Image of Colpitts oscillator LTspice simulation schematic]

> **提示**: 仿真文件位于 `/simulation/colpitts_v1.asc`，你可以下载后直接在 LTspice 中运行。

---

## 3. 硬件实现 (Hardware)
### 3.1 物料清单 (BOM)
| 元件 | 规格 | 数量 | 备注 |
| :--- | :--- | :--- | :--- |
| 三极管 | 2N2222 | 1 | NPN 型，高频特性好 |
| 电感 | 100µH | 1 | 建议使用低 ESR 电感 |
| 电容 | 100pF | 2 | 务必使用 NPO/C0G 材质以保证频率稳定 |
| 电阻 | 10k, 2k, 1k | 各1 | 1/4W 金属膜电阻 |

### 3.2 实测结果
使用 **Rigol DHO814** 示波器在 50Ω 负载下测得波形如下：

[Image of oscilloscope screen showing 2.8MHz sine wave with measurements]

---

## 4. 目录结构 (File Structure)
```text
01-colpitts-oscillator/
├── README.md              # 本说明文档
├── hardware/              
│   ├── schematics/        # 原理图 (PDF & KiCad 源文件)
│   └── bom/               # 物料清单 (CSV)
├── simulation/            
│   └── colpitts_v1.asc    # LTspice 仿真源文件
└── assets/                
    ├── waveform.png       # 示波器截图
    └── setup_photo.jpg    # 面包板接线实拍图