# Superdense Coding - Quantum Communication

This repository contains an implementation of **Superdense Coding**, a fundamental quantum communication protocol that allows Alice to send **two classical bits** to Bob by transmitting **only one qubit** using quantum entanglement.

---
## What is Superdense Coding?

Superdense coding is a **quantum communication protocol** that enables the transmission of **two classical bits** using **only one qubit**. It leverages the power of **quantum entanglement** and **quantum gates** to achieve **efficient information transfer**.

### **How It Works:**
1. **Entanglement Setup:** Alice and Bob share an **entangled qubit pair** in the Bell state.
2. **Encoding:** Alice applies quantum gates (**X, Z**) to her qubit based on the **2-bit classical message** she wants to send.
3. **Transmission:** Alice sends her modified qubit to Bob.
4. **Decoding:** Bob, using quantum gates (**CNOT, Hadamard**), retrieves the original **2-bit message** by measuring both qubits.

This technique effectively **doubles the classical information capacity** of a single qubit, demonstrating the power of quantum mechanics in communication.

---

## Overview

Superdense coding allows:

1. **Alice and Bob to share an entangled pair of qubits.**  
2. **Alice to apply quantum gates** to encode two classical bits onto her qubit.  
3. **Alice to send her qubit to Bob.**  
4. **Bob to apply decoding operations** to retrieve the original classical bits.  

This implementation uses **Qiskit** to build, simulate, and visualize the quantum circuit.

---

## 🛠 Installation

To run this project, install the required dependencies using:

```sh
pip install qiskit matplotlib
```

---

## Code Explanation

### 1️⃣ **Entanglement Creation (`create_entanglment_ckt`)**
- Creates an entangled Bell pair between Alice's and Bob’s qubits.
- Uses a **Hadamard (H) gate** followed by a **CNOT gate**.

### 2️⃣ **Encoding (`create_encoding_ckt`)**
- Alice applies **X and Z gates** to encode her **2-bit message** (`00`, `01`, `10`, `11`) into her qubit.

### 3️⃣ **Decoding (`create_decoding_ckt`)**
- Bob applies **CNOT and Hadamard gates** to decode Alice's message.

### 4️⃣ **Measurement (`measurement`)**
- Measures both qubits to retrieve the classical bits.

### 5️⃣ **Execution (`execute`)**
- Uses `AerSimulator()` to run the quantum circuit.

### 6️⃣ **Histogram Plotting (`plot_hist`)**
- Visualizes the measurement results as a histogram.

---

## How to Run

1. **Clone the repository:**
   ```sh
   git clone https://github.com/riitk/SuperDense-Coding.git
   cd SuperDense-Coding
   ```
2. **Run the script in Jupyter Notebook or Python:**
   ```sh
   python superdense_coding.py
   ```
3. **Enter one of the valid inputs:** `"00"`, `"01"`, `"10"`, `"11"`.

---

## Circuit Visualization

The quantum circuit is drawn using **Qiskit’s mpl drawer**.  
To display it properly in Jupyter Notebook, use:

```python
%matplotlib inline
q_ckt.draw("mpl")
```

---

## ⚠ Important Notes

- **Qiskit follows little-endian convention**, meaning qubit 0 is the least significant bit (LSB).
- Measurement results are **reversed**, so you may need to reverse the bitstrings using:
  ```python
  counts.reverse_bits()
  ```
  or manually:
  ```python
  fixed_counts = {key[::-1]: value for key, value in counts.items()}
  ```

---

## 📜 Example Output

```
Input: "10"
Output: {'10': 100}
```
This means that after decoding, Bob correctly received `10` with 100 shots.

---

## 🤝 Contributing

Feel free to submit issues or pull requests if you find improvements!

---

## 📜 References

- [Qiskit Documentation](https://qiskit.org/documentation/)
- [Superdense Coding (IBM Quantum)](https://quantum-computing.ibm.com/)

---

## 📜 License

This project is open-source under the **MIT License**.
