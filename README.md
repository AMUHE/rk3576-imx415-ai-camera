# rk3576-imx415-ai-camera

RK3576 + IMX415 AI Camera project.

This project is used to build an AI camera system based on the RK3576 platform and IMX415 image sensor.

## Project Goals

- Bring up IMX415 camera on RK3576
- Capture camera frames
- Process video stream
- Run AI inference on RK3576 NPU
- Display or save detection results
- Build a reproducible embedded AI camera demo

## Hardware

- SoC: Rockchip RK3576
- Camera Sensor: Sony IMX415
- Interface: MIPI CSI
- AI Accelerator: RK3576 NPU

## Software Plan

The project will be developed step by step:

1. Environment setup
2. Camera driver and device verification
3. Video capture test
4. RKNN model preparation
5. AI inference integration
6. Camera + AI pipeline
7. Performance optimization
8. Documentation and release

## Directory Structure

```text
rk3576-imx415-ai-camera/
├── assets/      # Images, diagrams, test media
├── configs/     # Configuration files
├── docs/        # Development notes and documents
├── models/      # AI models, ignored by git if large
├── scripts/     # Helper scripts
├── src/         # Source code
├── build/       # Build output, ignored by git
├── README.md
└── .gitignore
