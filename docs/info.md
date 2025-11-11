<!---

This file is used to generate your project datasheet. Please fill in the information below and delete any unused
sections.

You can also include images in this folder and reference them in the markdown. Each image must be less than
512 kb in size, and the combined size of all images must be less than 1 MB.
-->

## How it works

This design implements an 8-bit adder. It takes two 8-bit operands as inputs:
- **A[7:0]**: First operand provided on the `ui_in[7:0]` pins
- **B[7:0]**: Second operand provided on the `uio_in[7:0]` pins

The design performs a combinational addition operation: `SUM = A + B`, where the result is output on `uo_out[7:0]`. The addition is performed without a clock signal (combinational logic), so the output updates immediately when the inputs change.

Note: This is currently a template/example design. The sum may overflow beyond 8 bits, but only the lower 8 bits are output.

## How to test

To test this design:

1. **Set the inputs**: Apply two 8-bit values to the input pins:
   - Set `ui_in[7:0]` to the first operand (A)
   - Set `uio_in[7:0]` to the second operand (B)

2. **Read the output**: The sum `A + B` will appear on `uo_out[7:0]` immediately (combinational logic).

3. **Example test cases**:
   - A = 0x05 (5), B = 0x03 (3) → SUM = 0x08 (8)
   - A = 0xFF (255), B = 0x01 (1) → SUM = 0x00 (0, due to 8-bit overflow)
   - A = 0x42 (66), B = 0x2A (42) → SUM = 0x6C (108)

You can run the testbench using:
```sh
cd test
make -B
```

This will run the cocotb test suite and generate a VCD file (`tb.vcd`) that you can view with GTKWave or Surfer to verify the behavior.

## External hardware

List external hardware used in your project (e.g. PMOD, LED display, etc), if any
