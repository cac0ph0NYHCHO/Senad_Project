# CubeMX配置
## Pinout & Configuration

### System Core
#### GPIO
- PA0:作为TIM2_CH1复用输出口，输出PWM波形
#### RCC
- HSE:板子上自带的晶振
#### SYS
- Debug:SW，用STLink调试烧录
- 系统时钟：TIM6(基本定时器）

### Timers
#### TIM2
- Mode
  - Clock Source: Internal Clock
  - Channel1: PWM Generation CH1
- Configuration
  - Parameter Settings
    - ARR:(170M/800k = 212.5) - 1 = 211
  - DMA Settings: TIM2_CH1
    - Direction: Memory To Peripheral
    - Priority: `High`
  - GPIO Settings
    - GPIO mode: Alternate Function Push Pull
    - Maximum output speed: `High`

## Clock Configuration
- HCLK:170MHz(STM32G474RET6芯片的最大频率)


## Project Manager


## Tools


