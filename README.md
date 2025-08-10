# IEEE-754-Floating-Point-Adder
This project implements a **32-bit Single Precision Floating Point Adder** based on the **IEEE 754 Standard**, written in **Verilog HDL** and simulated using **Xilinx Vivado**. 
The project follows a **modular design approach** consisting of five main stages:
1. Unpacking the operands
2. Exponent alignment
3. Mantissa addition or subtraction
4. Normalization
5. Packing the result

---

## 🧠 Key Concepts

- **IEEE 754 Single Precision Format** (32 bits):
  - 1 bit sign
  - 8 bits exponent
  - 23 bits mantissa (with implicit leading 1)

- **Operations supported**:
  - Addition of two floating-point numbers (including signed values)
  - Automatic normalization and rounding (simple rounding)
  - Handles zero, signed numbers, and basic overflow

---

## 📁 Project Structure

FloatingPointAdder/
│
├── Floating_Point_Adder.v # Top-level module
├── Unpack_Operands.v # Extracts sign, exponent, mantissa
├── align.v # Aligns mantissas based on exponent difference
├── mantissa_add.v # Adds/subtracts the aligned mantissas
├── normalize.v # Normalizes the result after add/sub
├── pack.v # Packs the final result into IEEE 754 format
├── TB_FP_Adder.v # Testbench with 5 test cases


## 🔍 Simulation Results

All test cases are simulated using Vivado's simulator (`xsim`), and the waveform shows expected IEEE 754 encoded results for:

| **Test Case**                  | **Operand A** | **Operand B** | **Expected Result** |
|-------------------------------|---------------|---------------|---------------------|
| 1.0 + 2.0                     | `0x3F800000`  | `0x40000000`  | `0x40400000`        |
| 1.5 + 2.25                   | `0x3FC00000`  | `0x40200000`  | `0x40800000`        |
| -1.0 + 1.0                    | `0xBF800000`  | `0x3F800000`  | `0x00000000`        |
| -2.0 + -2.0                  | `0xC0000000`  | `0xC0000000`  | `0xC0800000`        |
| 0.0 + 5.5                    | `0x00000000`  | `0x40B00000`  | `0x40B00000`        |

✅ Output values match the expected IEEE 754 representations.

---

## 🛠️ How to Run

1. Open Xilinx Vivado.
2. Create a new Verilog project and add all source files and `TB_FP_Adder.v` testbench.
3. Run Behavioral Simulation.
4. Observe waveform outputs in the Vivado Simulator.

---

## 📌 Future Enhancements (Optional)

- Add support for:
  - Special cases: NaN, infinity, subnormal numbers
  - Rounding modes
  - Floating-point subtraction and multiplication
  - Pipeline architecture for performance

---

## 👨‍💻 Author

**Suraj Singh Bisht**  
B.Tech | Electronics and Communication Engineering (ECE)  
Project built as part of personal learning and Verilog practice.
