# main-project-ethernet-test

大项目前置验证子工程。用于硬件原型阶段的独立测试验证，功能稳定后再迁移进主项目。

## 当前进度

| 测试项 | 内容 | 状态 |
| --- | --- | --- |
| `uart1` | USART1 串口通信 | 已验证通过 |
| LAN8720 | 以太网 PHY（RMII） | 待调试 |
| RS485 | 半双工串口通信 | 待调试 |

## 硬件平台

- 主控：STM32F407VGT6，Mini 开发板（TypeC 口），1MB Flash，LQFP100
- 调试器：ST-LINK V2
- 串口：USART1，PA9（TX）/ PA10（RX），115200 8N1

## uart1 测试说明

- 工程目录：`uart1/`
- 开发环境：STM32CubeIDE
- 时钟配置：内部 HSI 经 PLL 倍频到 168MHz，不依赖外部晶振
- 预期现象：串口每秒输出一行 `UART communication works properly`

接线方式：

| USB 转 TTL | 开发板 |
| --- | --- |
| TX | PA10 |
| RX | PA9 |
| GND | GND |

串口参数：115200，8 位数据，无校验，1 位停止位。

## 后续计划

1. LAN8720 以太网：RMII 接口，验证链路、ping 与 TCP 通信
2. RS485：USART3（PD8 / PD9），方向控制 PD10，Modbus RTU 收发

## 仓库约定

- 仅使用 `main` 分支，不建开发分支
- 编译产物已在 `.gitignore` 中排除
- `.cproject`、`.project`、`.ioc`、`*.launch`、`.mxproject` 属于工程文件，需要提交

