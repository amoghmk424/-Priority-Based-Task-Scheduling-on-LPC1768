# Priority-Based Task Scheduling on LPC1768 (RTOS Simulation)

## Introduction
* This project demonstrates a Real-Time Operating System (RTOS)-like scheduler implemented on the LPC1768 microcontroller.
* The system executes five independent tasks using a priority-based round-robin scheduling mechanism.
* It simulates multitasking behavior without using an actual RTOS.
* Multiple peripherals such as LCD, UART, DC motor, stepper motor, and LED are interfaced.

## Objectives
* Implement priority-based scheduling
* Simulate RTOS behavior
* Execute multiple tasks concurrently
* Understand time slicing using SysTick timer
* Interface multiple hardware peripherals

## About LPC1768
* LPC1768 is a 32-bit microcontroller based on ARM Cortex-M3 architecture.
* It operates up to 100 MHz.
* It includes peripherals like UART, SPI, I2C, GPIO, ADC, PWM, and timers.
* It has a built-in SysTick timer used for scheduling.
* It is widely used in embedded systems and real-time applications.

## System Overview
* SysTick timer generates a 1 ms time base.
* Tasks are executed based on a scheduler.
* Priority array defines importance of each task.
* Round-robin ensures fairness in execution.

## Tasks Implemented
* Task_LCD:
  * Displays incrementing values on LCD periodically.

* Task_DC:
  * Controls DC motor operation continuously.

* Task_UART:
  * Sends formatted data through UART at regular intervals.

* Task_LED:
  * Toggles LED state every 500 ms.

* Task_Step:
  * Drives stepper motor in sequence.

## Scheduling Algorithm
* Priority-Based Round Robin Scheduling

* Priority Assignment:
  * LCD = 2
  * DC = 3
  * UART = 4
  * LED = 1
  * STEP = 2

* Execution Order:
  * UART → DC → LCD → STEP → LED

* Each task executes for a fixed time slice defined in the code.

## Working Principle
* SysTick timer generates periodic interrupts every 1 ms.
* A global counter (msTicks) tracks system time.
* Scheduler selects a task based on predefined order.
* Selected task executes until time slice expires.
* System resets outputs and switches to next task.

## Implementation Details
* Timing Control:
  * Implemented using SysTick_Handler.
  * msTicks variable stores system time.

* Peripheral Control:
  * GPIO used for LED, DC motor, and stepper motor.
  * UART used for serial communication.
  * LCD interfaced in 4-bit mode.

* Scheduler Logic:
  * schedule[] array determines execution order.
  * priority[] array defines importance.
  * switch-case structure executes tasks.

## Results
* LCD displays changing values.
* UART continuously transmits data.
* LED blinks at fixed intervals.
* DC motor runs continuously.
* Stepper motor rotates in sequence.
* Demonstrates multitasking and scheduling behavior successfully.

## Applications
* Embedded system learning
* RTOS concept demonstration
* Robotics control systems
* Industrial automation
* Real-time monitoring systems

## Future Scope
* Implement preemptive scheduling
* Integrate FreeRTOS
* Add interrupt-driven task switching
* Implement synchronization (semaphores, mutex)
* Add sensor-based tasks

## Conclusion
* The project successfully demonstrates an RTOS-like scheduler using LPC1768.
* It provides practical understanding of task scheduling and multitasking.
* It builds a strong foundation for advanced RTOS-based embedded system design.
