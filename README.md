# Altera CLI Tools 

This is a set of wrapper tools around around Altera Quartus to program altera FPGAs and 
specifically the DE1.

## Getting Started

These tools require that the Altera NIOS 

Usage of Altera CLI Tools
---

## `rompgm`
Program a ROM image `<ROM.rom>` into the DE1 Flash at address `<0xADDR>`

### Usage: 
`rompgm <ROM.rom> <0xADDR>`

* `<ROM.rom>` - Rom image file
* `<0xADDR>` - Address where to program it, must start with `0x`

### Steps:
1. Load NIOS into the FPGA (see `niosload`)
2. Convert the .rom file to a .flash file
3. Program the flash

### Notes:
After `rompgm` runs the board will still be running NIOS so a reset/power cycle may be required.

## `sofpgm`
Program a `.sof` file into the EPCS2 configuration device on the DE1 board

### Usage:
`sofpgm <input_sof.sof>`

* `<input_sof.sof>` -- sof file to be programmed into the EPCS2 configuration device

### Steps:
1. Generate a `.cof` file
2. Convert `.sof` to a `.jic` file
3. Generate a `.cdf` file
4. Program it into the EPCS2 device

### Notes:
After `sofpgm` runs the board will still be running programming mode so a reset/power cycle may be required.

## `sofload`
Load a `.sof` file into the FPGA

### Usage:
`sofpgm <input_sof.sof>`

* `<input_sof.sof>` -- sof file to be loaded into the FPGA
* 
### Steps:
1. Generate a `.cdf` file
2. Load it into the FPGA

### Notes:
* After `sofload` is run the board will immediately reset and start running the `.sof` file that was loaded.  
* The `.sof` file is loaded directly into the FPGA.  This will be lost if the board is reset/power cycled.  Use `sofpgm` to program the `.sof` file into the EPCS2 configuration device for a permanent load which will be persistent across reset/power cycle.

## `niosload`
Load Altera NIOS into the FPGA Board

### Usage: 
`niosload`

### Notes:
After `rompgm` runs the board will still be running NIOS so a reset/power cycle may be required to get back to anything that may be saved in the EPCS2 configuration device

