# STM32-pio-libs

## Overview

**STM32-pio-libs** is a collection of reusable libraries for **STM32Cube HAL** and **PlatformIO** based STM32 projects. Packages are published on [registry.platformio.org](https://registry.platformio.org/search?q=owner:anurag3301) and can be installed with `pio pkg`.

---

## Project Goal

This organization exists to provide **clean, reusable, and well-documented STM32 libraries** that can be dropped into application code without unnecessary friction.

The goals are:

* keep public APIs small and practical
* move drivers toward hardware-agnostic callback-based designs where it makes sense
* provide examples that show the intended integration pattern
* improve package-level documentation and repository consistency

Rather than treating each driver as a one-off code dump, the work here is to gradually move the libraries toward a more consistent and maintainable structure.

---

## Libraries

### Flash Storage

* [**W25Q64-flash**](https://github.com/STM32-pio-libs/W25Q64-flash)
  Hardware-agnostic driver for the W25Q64 8 MB SPI NOR flash chip. Callback-based SPI transport with no HAL dependency in the library itself. Covers read, write (with automatic page splitting), sector/block/chip erase, and deep power-down.

* [**W25Q64-lfs**](https://github.com/STM32-pio-libs/W25Q64-lfs)
  LittleFS block device adapter for W25Q64-flash. Single-call setup via `W25Q_LFS_BuildConfig`, static working buffers, no heap allocation. Pass the resulting `lfs_config` directly to `lfs_mount`.

* [**littlefs**](https://github.com/STM32-pio-libs/littlefs)
  Upstream LittleFS v2.11.3 repackaged as a PlatformIO library. Pulled in automatically as a transitive dependency of W25Q64-lfs.

### Display

* [**SSD1306**](https://github.com/STM32-pio-libs/SSD1306)
  Driver for SSD1306 OLED displays over I2C or SPI. Callback-based transport, full-screen and partial-region bitmap updates, and display control APIs (contrast, invert, power).

* [**gfx-mono**](https://github.com/STM32-pio-libs/gfx-mono)
  Lightweight monochrome graphics library for 1 bpp framebuffers. Pixels, rectangles, bitmap drawing, nearest-neighbor bitmap scaling, and scalable A–Z / 0–9 glyphs. A flush callback decouples it from any specific display IC — pairs naturally with SSD1306.

### Peripherals

* [**I2C-LCD**](https://github.com/STM32-pio-libs/I2C-LCD)
  Driver for HD44780-compatible character LCD modules connected through an I2C backpack (typically PCF8574). Callback-based I2C write and delay hooks. Cursor positioning, text output, custom CGRAM characters, backlight, and display controls.

* [**DS1302-RTC**](https://github.com/STM32-pio-libs/DS1302-RTC)
  Driver for the DS1302 real-time clock IC using GPIO bit-bang over CE/IO/SCLK. Individual and burst time/date accessors, 12/24-hour mode switching, and 31-byte battery-backed RAM read/write.

* [**NEO-6M**](https://github.com/STM32-pio-libs/NEO-6M)
  TinyGPS-style NMEA parser and interrupt-driven UART receive helper for the u-blox NEO-6M GPS module. Decodes RMC and GGA sentences: location, UTC date/time, speed, course, altitude, satellite count, HDOP, and fix quality.

### Utilities

* [**stm32-Delay**](https://github.com/STM32-pio-libs/stm32-Delay)
  Microsecond and millisecond delay functions for STM32Cube HAL projects.

---

## Reference Projects

* [**stm32f411-blackpill-base**](https://github.com/STM32-pio-libs/stm32f411-blackpill-base)
  Minimal PlatformIO project template for the STM32F411CE BlackPill board. Clock configured at 100 MHz over HSE with PLL, UART1 printf/scanf via syscall stubs. Use as a starting point for new BlackPill projects.

* [**F411-W25Q64-lfs-cli**](https://github.com/STM32-pio-libs/F411-W25Q64-lfs-cli)
  Interactive filesystem shell for the STM32F411CE BlackPill backed by a W25Q64 flash chip running LittleFS. Shell commands: `ls`, `lsr`, `cat`, `touch`, `mkdir`, `rm`, `cd`, `pwd`, `info`. Includes `pcfstool`, a Linux companion tool for transferring files to and from the board over UART.

---

## Who This Is For

These libraries are intended for developers working on:

* STM32Cube HAL projects
* PlatformIO-based STM32 firmware
* small and medium embedded applications that need straightforward reusable components

---

## Contribution

This is a practical, code-first organization. Bug reports, cleanup patches, example improvements, portability fixes, and documentation updates are all useful contributions.
