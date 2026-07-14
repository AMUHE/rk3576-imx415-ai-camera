# Day 02 - RK3576 Development Board Environment Check / 第 2 天 - RK3576 开发板环境检查

## Goal / 目标

Check the basic hardware and software environment of the RK3576 development board.

检查 RK3576 开发板的基础硬件与软件环境。

---

## Board Information / 开发板信息

- Board: DshanPI-A1 RK3576
- SoC: Rockchip RK3576
- Architecture: aarch64
- CPU: 8 cores
  - 4 × Cortex-A53
  - 4 × Cortex-A72
- Memory: 8GB LPDDR
- Storage: 64GB eMMC

---

## System Information / 系统信息

### Kernel / 内核

```text
Linux dshanpi-a1 6.1.115-vendor-rk35xx
```

This is a Rockchip RK35XX vendor-customized Linux 6.1 kernel.

这是 Rockchip RK35XX 原厂定制 Linux 6.1 内核。

### Distribution / 发行版

```text
100ASK_Armbian 25.11.0-trunk noble
Ubuntu 24.04 LTS, Noble Numbat
```

### Architecture / 架构

```text
aarch64, 64-bit ARM
```

The system supports both 32-bit and 64-bit programs.

系统支持 32 位和 64 位程序。

---

## CPU Information / CPU 信息

The RK3576 uses a standard 8-core big.LITTLE architecture.

RK3576 使用标准 8 核 big.LITTLE 架构。

```text
4 × Cortex-A53
4 × Cortex-A72
```

### Frequency Range / 频率范围

```text
Cortex-A53: 408 MHz ~ 2016 MHz
Cortex-A72: 408 MHz ~ 2208 MHz
```

### Instruction Features / 指令集特性

Supported instruction features include:

```text
fp asimd aes sha1 sha2 crc32
```

These features provide basic acceleration support for multimedia processing, encryption, and AI-related workloads.

这些指令特性可为多媒体处理、硬件加密以及 AI 相关任务提供基础加速支持。

---

## Memory Information / 内存信息

Result from `free -h`:

```text
Total memory:      7.7 GiB
Used memory:       857 MiB
Free memory:       3.9 GiB
Buffer/cache:      1.3 GiB
Available memory:  6.9 GiB
Swap:              0 B
```

The board has enough available memory for camera capture, image processing, and AI inference testing.

当前可用内存充足，适合进行摄像头采集、图像处理和 AI 推理测试。

---

## Storage Information / 存储信息

Result from `df -h`:

```text
Root filesystem / : 3.9G total, 781M used, 8% used
```

Temporary directories such as `/run` and `/tmp` are mounted as tmpfs and do not directly consume eMMC storage.

`/run` 和 `/tmp` 等临时目录使用 tmpfs，不直接占用 eMMC 空间。

Note:

Although the board has 64GB eMMC, the current root filesystem only shows about 3.9GB. This may be related to the current partition layout or system image configuration. It can be checked later using `lsblk`.

虽然开发板标称 64GB eMMC，但当前根分区只显示约 3.9GB，这可能与当前分区布局或系统镜像配置有关。后续可通过 `lsblk` 进一步确认。

---

## Camera Status / 摄像头状态

The current IMX415 CSI camera module has not been fully verified yet.

当前 IMX415 CSI 摄像头模块尚未完成验证。

Current situation:

- The camera connector/cable situation is uncertain.
- A 24-pin camera/cable was inserted into a 22-pin connector as a temporary fit.
- The current CSI module or connector may or may not be damaged.
- A new proper camera cable has been ordered.
- Camera testing will continue after the new cable arrives.
- The system may be re-flashed before the next camera bring-up test.

当前情况：

- 摄像头连接线/接口存在不确定因素。
- 曾将 24pin 摄像头/排线临时插入 22pin 底座接口。
- 当前 CSI 模块或底座接口是否损坏暂不确定。
- 已重新购买合适的数据线。
- 等待新数据线到货后继续测试摄像头。
- 后续可能重新烧录系统后再进行摄像头调试。

---

## Security Note / 安全备注

The system reports a Spectre v2 related warning due to unprivileged eBPF being enabled.

系统提示 Spectre v2 相关安全风险，原因与未特权 eBPF 开启有关。

This does not affect the current embedded vision development workflow.

该问题不影响当前嵌入式视觉项目开发流程。

---

## Notes / 备注

A command typo was noticed during the environment check:

```text
lscou
```

The correct command is:

```bash
lscpu
```

`lscpu` was executed successfully and used to confirm the CPU information.

---

## Summary / 总结

The RK3576 development board is running correctly with Ubuntu 24.04 based Armbian and Rockchip vendor Linux 6.1 kernel.

RK3576 开发板当前系统运行正常，使用基于 Ubuntu 24.04 的 Armbian 系统和 Rockchip 原厂 Linux 6.1 内核。

Confirmed environment:

```text
Board:   DshanPI-A1 RK3576
System:  100ASK_Armbian 25.11.0-trunk noble
Kernel:  Linux 6.1.115-vendor-rk35xx
CPU:     8-core, 4 × Cortex-A72 + 4 × Cortex-A53
Memory:  8GB LPDDR
Storage: 64GB eMMC
```

Camera bring-up is postponed until the correct CSI cable arrives.

摄像头调试将等待正确 CSI 数据线到货后继续。

---

## Next Step / 下一步

Day 03 tasks:

- Check storage partition layout with `lsblk`
- Check camera-related device nodes:
  - `/dev/video*`
  - `/dev/media*`
  - `/dev/v4l-subdev*`
- Check kernel camera logs with `dmesg`
- Re-flash the system if needed
- Retry IMX415 camera bring-up after receiving the correct CSI cable

Day 03 计划：

- 使用 `lsblk` 检查存储分区布局
- 检查摄像头相关设备节点：
  - `/dev/video*`
  - `/dev/media*`
  - `/dev/v4l-subdev*`
- 使用 `dmesg` 查看摄像头相关内核日志
- 如有必要，重新烧录系统
- 等待正确 CSI 数据线到货后重新测试 IMX415 摄像头
