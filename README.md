# Shor's 9-Qubit Quantum Error Correction Code

## Overview

Quantum information in qubits is fragile and susceptible to errors due to noise. Quantum error correction (QEC) addresses this by encoding data to shield it from disruptions, enabling detection and correction of errors like bit flips and phase flips. Shor’s 9-qubit code, one of the earliest QEC methods, uses nine physical qubits to protect a single logical qubit against any single-qubit error.

## Classical Error Correction

In classical systems, errors are often managed with repetition codes. For example, to send a bit with value \(1\), we might encode it as \(111\). Noise in the channel could flip a bit with probability \(p\), so if \(110\) is received, we can reasonably assume \(111\) was sent and decode it back to \(1\). This redundancy reduces error uncertainty in classical communication.

## Quantum Error Correction

Applying this to quantum systems is trickier due to several challenges:

- The no-cloning theorem: Quantum states can’t be copied exactly.
- Errors are continuous: Identifying specific errors requires high precision.
- Measurement disrupts quantum information.

## The Solution

Shor’s 9-qubit code overcomes these hurdles effectively.

The code encodes a logical qubit into nine physical qubits using a two-step process: a three-qubit code protects against phase flips, and each resulting qubit is then encoded with a three-qubit code for bit flips. This creates a robust nine-qubit structure. Here’s a simplified circuit demonstrating this principle with an initial qubit state:

<p align="center">
  <img src="shorcode_fixed.png" alt="Shor's Simplified Circuit" width="400"/>
</p>
<p align="center">
  <i>A simplified circuit showing an initial bit flip on q[0], followed by measurement. In the full Shor code, encoding, error introduction, correction, and decoding stages protect against bit and phase flips.</i>
</p>

In the full implementation, errors (e.g., a bit flip or phase flip) are introduced on one qubit. Error correction uses syndrome measurements to detect these without collapsing the logical state. Bit flips are identified by checking qubit pairs within three-qubit blocks, while phase flips are detected across the blocks. The process corrects any single-qubit error, restoring the original logical state, which is then decoded and measured.

To demonstrate, here are histograms showing measurement outcomes for initial states \(|0\rangle\) and \(|1\rangle\) after encoding, applying a bit flip and phase flip, correction, and decoding:

<p align="center">
  <img src="histogram0.png" alt="Histogram for |0>" width="300" style="display:inline-block;"/>
  <img src="histogram1.png" alt="Histogram for |1>" width="300" style="display:inline-block;"/>
</p>
<p align="center">
  <i>Left: Measurement outcomes for initial state |0〉, showing 1000 counts of '0'. Right: Outcomes for initial state |1〉, showing 1000 counts of '1'. Both confirm successful error correction.</i>
</p>
