# STM32-pio-libs

## Overview

**STM32-pio-libs** is a collection of reusable libraries for **STM32Cube HAL** and **PlatformIO** based STM32 projects.

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

## Repositories

* `SSD1306`  
  Driver for SSD1306 OLED displays. Supports the **SSD1306** controller over I2C and SPI, with a callback-based transport layer.

* `I2C-LCD`  
  Driver for HD44780-compatible character LCD modules connected through an I2C backpack, typically using a **PCF8574** I/O expander.

* `gfx-mono`  
  Lightweight monochrome graphics library for 1bpp framebuffers. This is a generic graphics helper and is **not tied to a specific IC**.

* `DS1302-RTC`  
  RTC library for the **DS1302** real-time clock IC, including time/date access and RAM read/write support.

* `HC-SR04`  
  Driver for the **HC-SR04** ultrasonic distance sensor.

* `NEO-6M`  
  UART-based helper library for the **u-blox NEO-6M** GPS module.

* `stm32-Delay`  
  Delay utility library for STM32Cube HAL projects. This is a **generic STM32 timing helper** and is not tied to a separate external IC.

---

## Current Work

The current effort in this organization is centered on improving older STM32 libraries so they match the quality of the newer ones.

That includes:

* removing fragile include-order dependencies
* replacing HAL-specific assumptions in public headers where possible
* adding complete examples
* writing proper documentation instead of placeholders
* making libraries easier to reuse across STM32 families

Recent work in this direction includes making the `I2C-LCD` driver hardware-agnostic in the same style as the `SSD1306` driver, with callback-based transport and dedicated examples.

---

## Who This Is For

These libraries are intended for developers working on:

* STM32Cube HAL projects
* PlatformIO-based STM32 firmware
* small and medium embedded applications that need straightforward reusable components

---

## Contribution

This is a practical, code-first organization. Bug reports, cleanup patches, example improvements, portability fixes, and documentation updates are all useful contributions.
