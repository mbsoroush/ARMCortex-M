# 🔌 ARM Cortex-M — Embedded Systems Exercises

A collection of seven hands-on embedded exercises for the **STM32F103C8T6** (ARM Cortex-M3). Each exercise is configured with **STM32CubeMX**, programmed in C with the STM32 HAL (built in **Keil uVision 5**), and tested in a **Proteus 8** simulation. Together they build up from simple GPIO output to timers, interrupts, and the ADC.

![ARM](https://img.shields.io/badge/Architecture-ARM%20Cortex--M-0091BD?style=flat-square)
![STM32](https://img.shields.io/badge/Platform-STM32F103C8T6-03234B?style=flat-square)
![STM32CubeMX](https://img.shields.io/badge/Tool-STM32CubeMX-03234B?style=flat-square)
![Keil](https://img.shields.io/badge/IDE-Keil%20uVision%205-00A98F?style=flat-square)
![Proteus](https://img.shields.io/badge/Simulation-Proteus%208-6A5ACD?style=flat-square)

## 📚 Exercises

| Folder | Exercise | What it does | Concepts |
|--------|----------|--------------|----------|
| [`01-led-chaser`](01-led-chaser) | LED chaser | A single lit LED sweeps back and forth across 8 LEDs on port A. | GPIO output, direct `ODR` access, bit shifting |
| [`02-seven-segment-counter`](02-seven-segment-counter) | Two-digit 7-segment counter | Counts from 00 to 59 on two common-cathode 7-segment displays (tens on port A, units on port B). | Lookup tables, driving multiple ports |
| [`03-lcd-scrolling-text`](03-lcd-scrolling-text) | LCD scrolling text | Scrolls a message across a 16x2 character LCD (HD44780 / LM016L). | LCD interfacing, string handling |
| [`04-lcd-stopwatch`](04-lcd-stopwatch) | LCD stopwatch | A stopwatch shown on the LCD with RUN / wait / STOP states, controlled by two push buttons. | External interrupts (EXTI), state flags |
| [`05-stepper-motor-control`](05-stepper-motor-control) | Stepper motor control | Drives a stepper motor with an 8-step half-step sequence. One button starts/stops it, the other reverses direction. | Half-step sequencing, EXTI callbacks |
| [`06-adc-voltage-threshold`](06-adc-voltage-threshold) | ADC voltage threshold | Reads an analog input on `PA0` (12-bit ADC, 3.3 V reference) and switches an output on `PA1` when the voltage exceeds 2.0 V. | ADC polling, voltage conversion |
| [`07-frequency-counter`](07-frequency-counter) | Frequency counter | Counts external pulses on `PA0` with **TIM2** (external clock mode) over a 1-second gate set by **TIM1**, then shows `Freq = N` on the LCD. | Timers, timer interrupts, external clock mode |

## ⚙️ Hardware & Tools

- **Microcontroller:** STM32F103C8T6 (ARM Cortex-M3, ARMv7-M)
- **Configuration & code generation:** STM32CubeMX
- **IDE / compiler:** Keil uVision 5
- **Simulation:** Proteus 8
- **Peripherals used:** GPIO, EXTI, ADC1, TIM1, TIM2, 16x2 character LCD, 7-segment displays, LEDs, push buttons, stepper motor

## 📁 Repository Structure

Every exercise folder follows the same layout:

```
NN-exercise-name/
├── main.c          # Application code (CubeMX-generated, with the exercise logic)
├── *.ioc           # STM32CubeMX configuration (pins, clocks, peripherals)
├── *.pdsprj        # Proteus 8 simulation project
└── *.hex           # Compiled firmware loaded into the Proteus simulation
```

> **Note:** Only the files above are included. The CubeMX-generated support files (HAL drivers, `Core/` sources, and the LCD library used by exercises 03, 04 and 07) are not part of this repository. To rebuild an exercise from source, open its `.ioc` in STM32CubeMX, regenerate the project, and add `main.c` and your LCD driver.

## 🚀 Getting Started

### Run the simulation (quickest)

1. Install **Proteus 8**.
2. Open the `.pdsprj` file inside an exercise folder.
3. Press **Play**. The matching `.hex` is already linked to the microcontroller.

### Rebuild the firmware

1. Open the exercise's `.ioc` file in **STM32CubeMX** and click **Generate Code** (select the Keil MDK-ARM toolchain).
2. Open the generated project in **Keil uVision 5**.
3. Replace the generated `main.c` with the one from this repository (and add the LCD driver for exercises 03, 04 and 07).
4. Build the project to produce a `.hex`, then load it into the Proteus microcontroller.

## 🧠 What You'll Learn

- Configuring an STM32 in CubeMX: pins, clock tree, NVIC, timers, and ADC
- Controlling GPIO through the HAL and directly through registers
- Handling external interrupts and timer interrupts with HAL callbacks
- Reading analog signals with the ADC and converting raw values to voltages
- Measuring frequency with timers in external clock mode
- Interfacing character LCDs, 7-segment displays, and stepper motors
- Simulation-based testing of embedded firmware before touching real hardware

## 🤝 Contributing

Suggestions and pull requests are welcome. Feel free to open an issue.
