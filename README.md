<div align="center">

# SDSZ · VisionMotion Lab

**北师大实验中学机器人校队**

让机器人看见世界，让想法真正动起来。

Computer Vision · Embedded Systems · Motion Control

[项目仓库](https://github.com/orgs/SDSZ-VisionMotion-Lab/repositories) · [系统文档](https://github.com/SDSZ-VisionMotion-Lab/gimbal-docs) · [快速入门](#快速入门)

</div>

---

## 我们是谁

我们来自**北京师范大学附属实验中学机器人校队**，是一群喜欢机器人、愿意动手解决问题的中学生。

在 VisionMotion Lab，我们围绕**视觉感知与运动控制**开展项目：从摄像头中的一帧图像，到开发板上的模型推理，再到云台与电机的响应，把算法、嵌入式软件和真实硬件连接起来。

这里记录我们的代码、实验与工程文档，也让每一次调试积累下来的经验，成为下一位队员继续探索的起点。

## 我们在做什么

- **视觉识别与追踪**：使用 YOLOv8、ByteTrack 等工具识别和跟踪目标，探索 OSTrack 单目标追踪。
- **板端模型部署**：围绕 RK3588 与 RKNN，将视觉推理接入实际机器人系统。
- **云台与底层控制**：结合 STM32、IMU、PID 与 CAN 电机通信，实现姿态控制和上、下位机协同。
- **工程实践与传承**：整理通信协议、部署步骤、联调方法和版本记录，让项目更容易理解、复现和接续开发。

目前的云台追踪项目围绕这条链路展开：

```text
USB 摄像头 → RK3588 视觉识别与目标追踪 → UART 控制指令 → STM32 云台与电机
                         ↑                                  │
                         └──────── 角度与状态反馈 ───────────┘
```

## 项目导航

| 项目 | 内容 | 阅读入口 |
| --- | --- | --- |
| [hitcar-rk3588](https://github.com/SDSZ-VisionMotion-Lab/hitcar-rk3588) | RK3588 视觉上位机：YOLOv8 / ByteTrack、目标锁定、图像误差到云台转速的转换及 UART 通信 | [上位机说明](https://github.com/SDSZ-VisionMotion-Lab/gimbal-docs/blob/main/upper/README.md) |
| [robot-platform-firmware](https://github.com/SDSZ-VisionMotion-Lab/robot-platform-firmware/tree/main) | 机器人底层固件：云台姿态控制、IMU、CAN 电机驱动与 UART 通信 | [下位机说明](https://github.com/SDSZ-VisionMotion-Lab/gimbal-docs/blob/main/lower/README.md) |
| [gimbal-docs](https://github.com/SDSZ-VisionMotion-Lab/gimbal-docs) | 云台系统文档：协议、代码阅读、部署、联调与配套版本记录 | [文档总入口](https://github.com/SDSZ-VisionMotion-Lab/gimbal-docs/blob/main/README.md) |
| [OSTrack-rk3588](https://github.com/SDSZ-VisionMotion-Lab/OSTrack-rk3588) | 基于上游 OSTrack 的单目标追踪研究仓库，面向 RK3588 部署探索 | [项目说明与上游来源](https://github.com/SDSZ-VisionMotion-Lab/OSTrack-rk3588/blob/main/README.md) |

当前与 RK3588 配套的 H7 固件位于 `robot-platform-firmware` 的 **main** 分支；**master** 分支保留 F407 工程。上位机与 H7 固件的系统文档集中维护在 `gimbal-docs`。

## 快速入门

第一次接触我们的项目，可以按下面的顺序阅读：

1. **先看整体**：[系统文档总入口](https://github.com/SDSZ-VisionMotion-Lab/gimbal-docs/blob/main/README.md)，了解上位机、下位机与文档项目的分工。
2. **沿着一帧图像读代码**：[两端实现阅读指南](https://github.com/SDSZ-VisionMotion-Lab/gimbal-docs/blob/main/implementation-guide.md)，理解视觉结果如何变成控制指令。
3. **开始部署与联调**：[RK3588 部署指南](https://github.com/SDSZ-VisionMotion-Lab/gimbal-docs/blob/main/deployment_rk3588.md) · [云台追踪与串口联调](https://github.com/SDSZ-VisionMotion-Lab/gimbal-docs/blob/main/gimbal_tracking.md)。
4. **查阅接口约定**：[UART 协议规范](https://github.com/SDSZ-VisionMotion-Lab/gimbal-docs/blob/main/protocol.md)，核对消息格式、单位与超时行为。

## 一起交流

欢迎对机器人、计算机视觉和嵌入式开发感兴趣的同学与开发者交流。

你可以在对应仓库提交 **Issue**，讨论问题、分享复现结果或提出改进建议；也欢迎通过 **Pull Request** 改进代码与文档。反馈部署或联调问题时，请尽量附上硬件型号、分支或提交号、运行配置和相关日志。

感谢开源社区提供的工具与研究成果。OSTrack 相关工作基于 [botaoye/OSTrack](https://github.com/botaoye/OSTrack)；各项目的使用与贡献请遵循对应仓库及上游项目的许可证。

---

<div align="center">

**从一帧图像，到一次运动。**  
在实验中学习，在协作中创造。

</div>
