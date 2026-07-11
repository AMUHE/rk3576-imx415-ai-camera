# rk3576-imx415-ai-camera

RK3576 + IMX415 AI Camera Project  
RK3576 + IMX415 AI 摄像头项目

---

## Overview / 项目简介

This project is used to build an AI camera system based on the Rockchip RK3576 platform and the Sony IMX415 image sensor.

本项目用于构建一个基于 Rockchip RK3576 平台和 Sony IMX415 图像传感器的 AI 摄像头系统。

The final goal is to capture video from the IMX415 camera, process image frames, run AI inference on the RK3576 NPU, and output detection or analysis results.

最终目标是从 IMX415 摄像头采集视频，对图像帧进行处理，在 RK3576 NPU 上运行 AI 推理，并输出检测或分析结果。

---

## Project Goals / 项目目标

- Bring up the IMX415 camera on the RK3576 platform  
  在 RK3576 平台上调通 IMX415 摄像头

- Capture camera frames from the video device  
  从视频设备节点采集摄像头图像帧

- Process video stream in real time  
  对视频流进行实时处理

- Run AI inference using the RK3576 NPU  
  使用 RK3576 NPU 进行 AI 推理

- Display, save, or stream AI detection results  
  显示、保存或推流 AI 检测结果

- Build a reproducible embedded AI camera demo  
  构建一个可复现的嵌入式 AI 摄像头演示项目

---

## Hardware / 硬件平台

| Item | Description |
|---|---|
| SoC / 主控 | Rockchip RK3576 |
| Camera Sensor / 摄像头传感器 | Sony IMX415 |
| Camera Interface / 摄像头接口 | MIPI CSI |
| AI Accelerator / AI 加速器 | RK3576 NPU |
| Target Device / 目标设备 | RK3576 development board |

---

## Software Plan / 软件开发计划

The project will be developed step by step.

本项目将按照以下步骤逐步开发。

1. Environment setup  
   开发环境搭建

2. Camera driver and device verification  
   摄像头驱动和设备节点验证

3. Video capture test  
   视频采集测试

4. RKNN model preparation  
   RKNN 模型准备

5. AI inference integration  
   AI 推理集成

6. Camera + AI pipeline integration  
   摄像头采集与 AI 推理流程整合

7. Performance optimization  
   性能优化

8. Documentation and release  
   文档整理与项目发布

---

## Directory Structure / 目录结构

```text
rk3576-imx415-ai-camera/
├── assets/      # Images, diagrams, test media / 图片、示意图、测试媒体
├── configs/     # Configuration files / 配置文件
├── docs/        # Development notes and documents / 开发记录和文档
├── models/      # AI models / AI 模型文件
├── scripts/     # Helper scripts / 辅助脚本
├── src/         # Source code / 源代码
├── build/       # Build output, ignored by git / 编译输出目录，不提交到 Git
├── README.md    # Project introduction / 项目说明
└── .gitignore   # Git ignore rules / Git 忽略规则
