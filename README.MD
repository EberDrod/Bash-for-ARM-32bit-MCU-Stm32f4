# 💡 Blink para STM32F4 (Nucleo o Discovery) en macOS

Este es un proyecto básico que hace parpadear un LED (verde o azul) en una placa STM32F4 (como la Nucleo-F401RE o la Discovery STM32F407G). Está pensado para usarse con herramientas libres desde una MacBook, sin depender de STM32CubeIDE.

---

## 🧩 Requisitos

Antes de compilar o flashear, instala estas herramientas en tu Mac.

### ✅ Paso 1: Instala Homebrew

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"


### ✅ Paso 2: Instala Dependencias para STM32F4

brew tap ArmMbed/homebrew-formulae
brew install arm-none-eabi-gcc
brew install stlink

### ✅ Paso 3: Drivers

https://github.com/STMicroelectronics/STM32CubeF4/archive/refs/heads/master.zip



### ✅ Paso 4: Estructura de Proyecto basico antes de compilacion 


stm32-blink/
├── main.c                    ← Código fuente (LED azul o verde)
├── startup_stm32f4xx.s      ← Archivo de inicio mínimo
├── linker.ld                ← Script de linker para STM32F4
├── Makefile                 ← Compilación con make
└── build_and_flash.sh       ← Script para compilar y flashear automáticamente

### ✅ Paso 5: Genera BINARIOS .HEX ´+ ARCHIVOS 
Make clean && make 



### ✅ Paso 6: Estructura de Proyecto basico antes de compilacion 
make flash
openocd -f interface/stlink.cfg -f target/stm32f4x.cfg -c "program blink.hex verify reset exit"
Open On-Chip Debugger 0.12.0
Licensed under GNU GPL v2
For bug reports, read
	http://openocd.org/doc/doxygen/bugs.html
Info : auto-selecting first available session transport "hla_swd". To override use 'transport select <transport>'.
Info : The selected transport took over low-level target control. The results might differ compared to plain JTAG/SWD
Info : clock speed 2000 kHz
Info : STLINK V2J37M27 (API v2) VID:PID 0483:374B
Info : Target voltage: 2.884792
Info : [stm32f4x.cpu] Cortex-M4 r0p1 processor detected
Info : [stm32f4x.cpu] target has 6 breakpoints, 4 watchpoints
Info : starting gdb server for stm32f4x.cpu on 3333
Info : Listening on port 3333 for gdb connections
Info : Unable to match requested speed 2000 kHz, using 1800 kHz
Info : Unable to match requested speed 2000 kHz, using 1800 kHz
[stm32f4x.cpu] halted due to debug-request, current mode: Thread 
xPSR: 0x01000000 pc: 0x080007ec msp: 0x20020000
Info : Unable to match requested speed 8000 kHz, using 4000 kHz
Info : Unable to match requested speed 8000 kHz, using 4000 kHz
** Programming Started **
Info : device id = 0x10076413
Info : flash size = 1024 KiB
** Programming Finished **
** Verify Started **
** Verified OK **
** Resetting Target **
Info : Unable to match requested speed 2000 kHz, using 1800 kHz
Info : Unable to match requested speed 2000 kHz, using 1800 kHz
shutdown command invoked



### ✅ Connecta tu placa & Verifica que tenga ok 

st-info --probe
Found 1 stlink programmers
  version:    V2J37S27
  serial:     0671FF535353897167074745
  flash:      1048576 (pagesize: 16384)
  sram:       196608
  chipid:     0x413
  dev-type:   STM32F4x5_F4x7