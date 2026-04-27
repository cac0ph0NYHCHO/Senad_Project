**TIPS:**
- 形如`*待定内容*`的为未确定内容，正在Debug


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
    - ARR:(170M/800k = 212.5) - 1 = 212
  - DMA Settings: TIM2_CH1
    - Direction: Memory To Peripheral
    - Priority: `*High*`
  - GPIO Settings
    - GPIO mode: Alternate Function Push Pull
    - Maximum output speed: `*High*`

### Middleware and Software Packs: FREERTOS
- Mode
  - CMSIS_V2
- Configuration
  - Tasks and Queues
    - defaultTask
      - Stack Size: `*512*` Words
  - Advanced settings
    - USE_NEWLIB_REENTRANT: `*Disabled*`


## Clock Configuration
- HCLK:170MHz(STM32G474RET6芯片的最大频率)


## Project Manager


## Tools



# CubeMX生成后Keil5的设置
- 魔术棒 --> Target--Code Generation --> ARM Compiler--version6
- 删除原来的port.c文件，添加桌面ARM_CM4F文件夹里的port.c文件
- 魔术棒 --> C/C++ --> Include Paths --> 删除原来的portable/RVDS/ARM_CM4F路径，把桌面的ARM_CM4F文件夹拖进`..\Middlewares\Third_Party\FreeRTOS\Source\portable`路径下，并选中添加到头文件路径中

# 测试流程
- (完成)先打开PC6控制LED1测试RTOS环境是否配置成功：成功！
- (完成)开启PC3口输出翻转电平，学习示波器的使用，确实这示波器不太好用
- (待定)改变主频72MHz,ARR改成89，WS2812里数据0变成25，数据1变成60，dma数据变成half word
- (完成)PC0接收按键输入信号，控制PC6-LED1翻转电平
- ()继续完成灯带的开发
