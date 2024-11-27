
# Port Driver (AUTOSAR 4.0.3)

This repository contains the implementation of the `Port` driver module for the TM4C123GH6PM microcontroller following the AUTOSAR 4.0.3 standard. The module is developed in C using the IAR Embedded Workbench IDE.

![Logo](https://github.com/user-attachments/assets/d6258306-5c5b-4ad6-9327-88d452ae10f6)


## Features
- Configurable GPIO pins for various peripherals (UART, SSI, I2C, etc.).
- Supports direction and mode changeability for pins.
- Provides APIs for port initialization, pin direction/mode configuration, and more.
- Includes standard error handling via AUTOSAR's DET (Development Error Tracer).

## Files
- **`Port.h`**: Header file defining data structures, macros, and APIs for the Port driver.
- **`Port.c`**: Source file containing the implementation of the Port driver APIs.
- **`Port_Cfg.h`**: Configuration file to define pin configurations specific to your application.
- **`Port_PBcfg.h`**:  Post Build Configuration Source file for TM4C123GH6PM Microcontroller - Port Driver
- **`Port_Regs.h`**: Header file for TM4C123GH6PM Microcontroller - Port Driver Registers
  
## How to Use
1. **Configure the pins in `Port_Cfg.h`**: Define the pins to be used and their attributes such as direction, mode, and internal resistors.
2. **Initialize the Port Driver**: Call the `Port_Init()` function in your application, passing the configuration data.
3. **Set Pin Direction/Mode**: Use `Port_SetPinDirection()` and `Port_SetPinMode()` to control pin configurations dynamically.
4. **Refresh Pin Direction**: If needed, the `Port_RefreshPortDirection()` function can be used to restore the direction of pins to their initial configuration.

## Example Configuration in `Port_Cfg.h`
Here is an example of how to configure a GPIO pin:

```c
/* Number of the configured Port Channels */
#define PORT_CONFIGURED_PINS                    (39U)

/* Pin Index in the array of structures in Port_PBcfg.c */
#define PortConf_PA1_PIN_ID_INDEX        (uint8)0x01

/* PORT Configured Port Numbers  */
#define PortConf_PA1_PORT_NUM        (uint8)0

/* 
 * PORT Configured Pin Modes 
 * by default all pins are configured as GPIO 
 */
#define PortConf_PA1_PIN_MODE         (Port_PinMode)GPIO

/* 
 * PORT Configured Pin Internal Resistor 
 * by default all pins are configured as inputs in pull-up configuration,
 * except for LED at PF1 is output  
 */
#define PortConf_PA1_PIN_INTERNAL_RESISTOR         (Port_InternalResistorType)PULL_UP

/* 
 * PORT Configured Pin Initial Value 
 * by default all pins are configured as inputs so the have no initial value,
 * except for LED at PF1 is output with initial value = STD_LOW  
 */
#define PortConf_PA1_PIN_INITIAL_VALUE         STD_LOW

/* 
 * PORT Configured Pin Direction changeability
 * by default all pins are changeable  
 */
#define PortConf_PA1_PIN_DIRECTION_CHANGE         STD_ON

/* 
 * PORT Configured Pin Mode changeability
 * by default all pins are changeable  
 */
#define PortConf_PA1_PIN_MODE_CHANGE         STD_ON

```

## Available APIs
- **`Port_Init()`**: Initializes the Port driver with the provided configuration data.
- **`Port_SetPinDirection()`**: Sets the direction (input/output) for a specified pin.
- **`Port_SetPinMode()`**: Sets the mode (e.g., GPIO, UART) for a specified pin.
- **`Port_RefreshPortDirection()`**: Refreshes the pin direction to its original configured value.
- **`Port_GetVersionInfo()`**: Returns the version information of the Port module.

