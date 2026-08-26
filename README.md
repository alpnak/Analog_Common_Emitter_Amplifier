# 4-Stage Analog Common Emitter Amplifier Design and Analysis With LTspice & KiCad

This project details the end-to-end design of a four-stage audio amplifier, developed as part of the Analog Electronic Circuits project. The work spans theoretical mathematical analysis, detailed SPICE simulations, physical breadboard prototyping, and a final industrial-standard PCB design. By meticulously documenting the analytical computations, simulation data, and real-world test results, this repository is structured to serve as a robust, open-source foundation for upcoming theoretical electricity and electronics educational content‚ Äî specifically designed to be produced using computer graphics and text-to-speech tools rather than traditional camera recordings.

## Project Phases

### Phase 1: Common Emitter (CE) Stage Design
**Objective:** Design the foundational first gain stage of the audio amplifier using a Common Emitter configuration to provide high voltage gain.

**Details:** This initial phase focuses on establishing a stable DC operating point, performing AC small-signal analysis, and calculating the upper and lower cutoff frequencies for a band-pass characteristic. Utilizing ideal transistor parameters ($ eta = 180$) and a $\pm 15V$ dual supply, the stage is engineered to deliver a targeted voltage gain ($|A_v| \ge 30$) and an output voltage swing of 22-24V peak-to-peak. The design ensures the frequency response encompasses the standard audio band ($f_L \le 20 	ext{ Hz}$, $f_H \ge 20 	ext{ kHz}$) and is thoroughly verified through LTspice simulations (.op, .ac, .tran).

![Phase 1 Schematic](faz1.png)

### Phase 2: Emitter Follower (EF) and Multistage Cascading
**Objective:** Introduce an Emitter Follower (buffer) stage to prevent loading effects between stages and successfully transition into a multistage cascaded architecture.
**Details:** To meet higher amplification requirements, the system is expanded by cascading two Common Emitter stages followed by an Emitter Follower stage. This configuration acts as a buffer, ensuring proper impedance matching and preserving the signal integrity across stages. The selection of appropriate inter-stage coupling capacitors is critical here to maintain the 20 Hz - 20 kHz audio band requirements. The combined multistage system is designed to achieve a total voltage gain of $A_v \ge 200$ and a maximum output swing exceeding 20V peak-to-peak, all while maintaining strict power dissipation limits for each resistor ($< 0.2W$).

![Phase 2A Schematic](faz2A.png)
![Phase 2B Schematic](faz2B.png)

### Phase 3: Class AB Power Stage, Real Transistor Selection, and Full System Integration
**Objective:** Design a Class AB push-pull output stage capable of driving an $8 \Omega$ speaker load, transition from ideal SPICE models to real-world commercial BJTs, and finalize the complete 4-stage architecture.
**Details:** The final system architecture consists of two CE gain stages, one EF buffer stage, and a Class AB power output stage. This phase involves extensive datasheet analysis to replace the initial ideal transistors with physical components that meet the required thermal stability, current capacity, and gain bandwidth products. The Class AB stage utilizes a complementary push-pull pair with diode biasing to eliminate crossover distortion. The finalized full system targets a total voltage gain of $> 1000$ and an output power of $\ge 2	ext{W}$ over the $8 \Omega$ load, while keeping total system power consumption under 10W.

**Components Selected in this Phase:**
*   **Input and Intermediate Gain Stages (CE):** `BC546B` (Chosen for high $V_{CEO}$ breakdown voltage and stable current gain).
*   **Driver / Buffer Stage (EF):** `BD139-16` (Selected for its thermal stability and medium-power endurance).
*   **Power Stage (Class AB Push-Pull):** `BD139` (NPN) & `BD140` (PNP) complementary pair.
*   **Biasing:** `1N4148` fast-switching diodes.

![Phase 3 Schematic](insert_image_link_here)

### Phase 4: Physical Implementation, Measurement, and PCB Design
**Objective:** Validate the theoretical and simulated designs in the physical world and convert the validated circuit into a professional printed circuit board (PCB).
**Details:** The complete amplifier is prototyped on a breadboard to assess real-world performance against parasitic effects, thermal drift, and component tolerances. Key metrics, including DC offset, signal gain, output power, and frequency response, are physically measured using an oscilloscope and multimeter. Following successful breadboard validation, a 2-layer (Top & Bottom) PCB layout is designed using KiCad EDA. The PCB design adheres to strict design rules, incorporating minimum trace widths for power (1 mm) and signal lines (0.3 mm), as well as dedicated thermal relief (heat sink) zones for the power transistors, ensuring a zero-error Design Rules Check (DRC).

![Phase 4 Schematic and PCB](insert_image_link_here)