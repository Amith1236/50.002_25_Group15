# Lab 3 - Digital Logic Design

This lab implements various digital logic modules for a processor design, including ALU components, display drivers, and control logic.

## Module Overview

### ALU Components

#### Adder Module (`adder.luc`)
- Implements a 32-bit adder with overflow detection
- Supports both signed and unsigned addition
- Generates zero, overflow, and negative flags
- Used as a core component in the ALU

#### Compare Module (`compare.luc`)
- Implements comparison operations using status flags
- Supports three comparison types:
  - CMPEQ (Equal)
  - CMPLT (Less Than)
  - CMPLE (Less Than or Equal)
- Uses zero, overflow, and negative flags from the adder

#### Bit Operations

##### Bit Reverse Module (`bit_reverse.luc`)
- Reverses the order of bits in a given input value
- Parameterized for configurable bit width (default: 32 bits)
- Useful for data transformations and endianness conversions

##### Shifter Modules
- `shifter.luc`: Base shifter module with configurable bit width
- `x_bit_left_shifter.luc`: Left shift by a specified number of bits
- `x_bit_right_shifter.luc`: Right shift by a specified number of bits
- Supports both logical and arithmetic shifts

### Multiplexers

#### 2-to-1 MUX (`mux_2.luc`)
- Simple 2-input multiplexer
- Selects between two inputs based on a control signal

#### 4-to-1 MUX (`mux_4.luc`)
- 4-input multiplexer
- Uses 2-bit control signal to select one of four inputs

### Display Drivers

#### Seven Segment Display (`seven_seg.luc`)
- Converts 4-bit hexadecimal input to 7-segment display pattern
- Supports digits 0-9 and letters A-F
- Each bit in the output controls a specific segment of the display

#### Multi-Seven Segment Display (`multi_seven_seg.luc`)
- Drives multiple 7-segment displays using time-division multiplexing
- Parameterized for number of digits and refresh rate
- Uses a counter to cycle through displays
- Includes digit selection logic for multiplexing

## Module Dependencies

```
adder.luc
    └── compare.luc
        └── alu.luc

shifter.luc
    ├── x_bit_left_shifter.luc
    └── x_bit_right_shifter.luc
        └── alu.luc

mux_2.luc
    └── mux_4.luc
        └── alu.luc

seven_seg.luc
    └── multi_seven_seg.luc
```

## Usage

Each module is designed to be used as part of a larger processor design. The modules can be instantiated and connected to create the complete system. Key features include:

- Parameterized designs for flexibility
- Clear input/output interfaces
- Comprehensive error handling
- Efficient implementation of digital logic operations

## Implementation Details

- All modules are written in Lucid HDL
- Use synchronous design principles where appropriate
- Include detailed comments for maintainability
- Follow modular design practices for reusability
