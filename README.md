# Shor's 9-Qubit Quantum Error Correction Code

## Overview

Shor’s 9-qubit code is a quantum error correction method that protects a single logical qubit using nine physical qubits. Developed by Peter Shor, it encodes the logical state—starting as \(|\psi\rangle = \alpha|0\rangle + \beta|1\rangle\)—into a nine-qubit configuration through a series of CNOT and Hadamard gates. This setup shields the qubit from noise by redundantly spreading the information, allowing detection and correction of errors that disrupt quantum systems.

## The Solution

Unlike simpler codes that handle only bit flips, Shor’s 9-qubit code detects and corrects both bit flips and phase flips within the same circuit. After encoding, the circuit introduces a bit flip (\(X\)) and phase flip (\(Z\)) on one qubit to simulate noise. Correction uses syndrome measurements—checking qubit pairs for bit errors and block relations for phase errors—to identify and fix these disruptions. Decoding then retrieves the original state, measured to verify correction.

The simplified circuit below shows an initial state setup and measurement:

<p align="center">
  <img src="shorcode_fixed.png" alt="Shor's Simplified Circuit" width="400"/>
</p>
<p align="center">
  <i>A basic circuit applying an X gate to q[0] followed by measurement. The full Shor code includes encoding, error simulation, correction, and decoding stages.</i>
</p>

Below are histograms showing results for initial states \(|0\rangle\) and \(|1\rangle\) after the full process:

<p align="center">
  <img src="histogram0.png" alt="Histogram for |0>" width="300" style="display:inline-block;"/>
  <img src="histogram1.png" alt="Histogram for |1>" width="300" style="display:inline-block;"/>
</p>
<p align="center">
  <i>Left: Results for initial state |0〉, yielding 1000 counts of '0'. Right: Results for initial state |1〉, yielding 1000 counts of '1'. These confirm the code’s error correction.</i>
</p>
