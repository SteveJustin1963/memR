# Experimenter 1 — TEC‑1 memR Add‑On Board Kit

**Working name:** Experimenter 1  
**Project base:** `memR-main.zip` / tec‑memR project files  
**Board concept:** 250 mm × 200 mm educational experimenter PCB  
**Style:** Maxitronix / 130‑in‑1 style patch‑wire lab, but aimed at TEC‑1 / Z80, MINT, analog computing, memristor experiments, Lissajous figures, and phase‑coded neural computation.

---

## 1. Concept in One Sentence

Build a large reusable add‑on board for the TEC‑1 Z80 that lets a user patch together oscillators, phase shifters, analog summers, ADC/DAC blocks, digital latches, memristor/emulator cells, and a 4×4 crossbar using jumper wires, then enter small Z80 programs through the TEC‑1 hex keypad to run experiments.

The board should feel like an electronics lab kit, not like a single fixed circuit.

The user should be able to:

1. Plug the board into the TEC‑1 expansion connector.
2. Patch labelled terminals with jumper wires.
3. Enter a short Z80 machine‑code program using the TEC‑1 hex keypad.
4. Press run.
5. Watch LEDs, a speaker, an oscilloscope trace, or ADC values respond.
6. Move wires and discover a new experiment.

---

## 2. Design Goals

### Main goals

- **Educational:** each section teaches one idea clearly.
- **Patchable:** jumper wires connect blocks like a 130‑in‑1 electronics lab.
- **TEC‑1 friendly:** experiments can be driven by short Z80 code entered by hex keypad.
- **Analog + digital:** Z80 control plus real analog wave behaviour.
- **Expandable:** real memristors can be added later, but stable emulators work first.
- **Sellable as a kit:** board, parts, manual, jumper leads, experiment cards.

### What makes it different

Most electronics lab kits teach individual circuits. This one teaches a system:

> **Phase = Weight. Interference = Computation. Z80 = Experiment Controller.**

The user starts with basic electronics, then walks toward:

- oscillators
- Lissajous figures
- phase shift
- analog summing
- ADC/DAC interfacing
- memristor testing
- crossbar arrays
- simple neural / logic experiments
- optional photonic/fibre experiments

---

## 3. Important Safety Limits

This kit should be designed as a **low‑voltage educational device only**.

### Hard limits

- No mains wiring on the board.
- No exposed voltages above about 12 V in the base kit.
- Use current limiting on every memristor / experimental material connection.
- Use fuses or resettable polyfuses on external power inputs.
- Do not include high‑power lasers in the base kit.
- If selling in Australia, check product safety, EMC, battery, labelling, and chemical packaging rules before release.

### Recommended safe power inputs

- 5 V from TEC‑1 / USB only for digital logic.
- Optional 9–12 V DC plugpack for analog experiments.
- Optional dual rail generation on board: ±5 V or ±9 V, current limited.

### Chemistry note

The copper‑sulphide DIY memristor idea is interesting, but do **not** make the first commercial kit depend on it. Use a stable memristor emulator first. Treat the real memristor area as an optional advanced lab with clear warnings.

---

## 4. Board Format

### Target board size

- **Width:** 250 mm
- **Height:** 200 mm
- **Mounting:** four or six 3 mm mounting holes
- **Board type:** 2‑layer possible, 4‑layer preferred if budget allows
- **Silkscreen:** very important; this board lives by labels

### Recommended physical style

Use a large PCB with:

- labelled patch points
- terminal numbers
- module boxes printed on silkscreen
- LEDs beside logic outputs
- test points for oscilloscope probes
- a permanent experiment number grid printed on the board
- optional plastic overlay / printed experiment cards

Use jumper styles such as:

- 2.54 mm Dupont pins for cheap kits
- 2 mm banana / spring terminals for a premium kit
- mixed style: pin headers on PCB, spring‑clip adapter board for classroom version

---

## 5. 250 × 200 mm PCB Segment Layout

Coordinate origin: top left of board.

| Zone | Approx area | Name | Purpose |
|---|---:|---|---|
| A | 0–250 × 0–20 mm | Power rail strip | 5 V, analog supply, virtual ground, fuses, LEDs |
| B | 0–45 × 20–115 mm | TEC‑1 / Z80 interface | bus connector, buffers, decode logic |
| C | 0–45 × 115–200 mm | Code / monitor helper | printed port map, hex byte tables, run notes |
| D | 45–120 × 20–75 mm | Oscillator bank | 555, Wien bridge, DDS/NCO input, speaker output |
| E | 120–170 × 20–75 mm | Clock / timing / burst | gates, one‑shots, trigger pulses, burst maker |
| F | 45–170 × 75–130 mm | Patch bay | central jumper field, labelled nodes |
| G | 45–120 × 130–200 mm | Phase shifter lab | all‑pass filters, digital pot socket, varactor test |
| H | 120–170 × 130–200 mm | Interference neuron | summer, mixer, envelope detector, comparator |
| I | 170–250 × 20–80 mm | ADC / DAC / latch area | DAC0808/MCP4725, ADC0804/MCP3008, latches |
| J | 170–250 × 80–145 mm | Memristor / emulator bay | plug‑in cell, CuS pads, resistor emulator, digital pot |
| K | 170–250 × 145–200 mm | 4×4 crossbar / outputs | row/column mux, LED bargraph, scope headers |

### ASCII board view

```text
250 mm wide
┌──────────────────────────────────────────────────────────────────────┐
│ A POWER: +5V  GND  VREF  +ANA  -ANA  FUSE  SWITCH  POWER LED          │ 20
├───────────────┬─────────────────────┬──────────────┬────────────────┤
│ B TEC‑1 / Z80 │ D OSCILLATORS       │ E TIMING     │ I ADC/DAC      │
│ BUS + DECODE  │ 555 / WIEN / DDS    │ BURST/GATES  │ LATCHES        │
│ PORT 10‑17h   │ SINE/SQUARE/AUDIO   │ TRIGGER      │                │
├───────────────┼─────────────────────┴──────────────┼────────────────┤
│ C CODE CARDS  │ F CENTRAL PATCH BAY                  │ J MEMRISTOR /  │
│ HEX BYTES     │ numbered jumper terminals             │ EMULATOR BAY   │
│ PORT MAP      │                                      │                │
├───────────────┼─────────────────────┬──────────────┼────────────────┤
│ MONITOR NOTES │ G PHASE SHIFTERS    │ H SUM/MIX/   │ K 4×4 CROSSBAR │
│               │ ALL‑PASS/VARACTOR   │ ENVELOPE     │ LED/SCOPE OUT  │
└───────────────┴─────────────────────┴──────────────┴────────────────┘
200 mm high
```

---

## 6. The Board as Sellable Kit Segments

Do not sell the whole idea as one confusing object. Sell it in layers.

### Kit 1 — Experimenter 1 Base Kit

This is the main 250 × 200 board.

Includes:

- PCB
- TEC‑1/Z80 interface parts
- power section
- patch bay
- oscillator section
- basic phase shifter
- summer / detector
- ADC/DAC basic interface
- LEDs, speaker, jumper wires
- printed manual / experiment cards

Purpose:

- makes sound
- makes waves
- makes Lissajous patterns
- lets Z80 read and write analog values
- lets beginners enter small hex programs and see results

### Kit 2 — Memristor Emulator Pack

Includes:

- digital potentiometer board
- resistor ladder plug‑ins
- 4×4 pseudo‑crossbar plug‑in
- calibration card

Purpose:

- stable repeatable experiments
- phase weight storage simulation
- matrix / neural experiments without fragile chemistry

### Kit 3 — Real Memristor Advanced Pack

Includes:

- replaceable memristor carrier cards
- copper pads
- aluminium probe wires
- current‑limit resistors
- clip leads
- warning sheet

Do **not** rely on this pack for the first success experience. It should be advanced / optional.

### Kit 4 — Photonic / Fibre Demo Pack

Includes:

- LED or safe low‑power laser module
- photodiode receiver
- fibre / light pipe demo
- optional piezo stretcher fixture

Purpose:

- show that the same phase/interference logic can move toward optics later

### Kit 5 — Classroom / Workshop Pack

Includes:

- 6 boards
- 6 jumper sets
- instructor manual
- spare ICs
- laminated experiment cards
- fault‑finding guide

---

## 7. Electrical Architecture

### Core signal flow

```text
TEC‑1 / Z80
   │
   ├── OUT port → latch / DAC / mux select
   │
   ├── IN port  ← ADC / comparator / detector
   │
   ↓
Patchable analog board
   │
   ├── oscillator → phase shifter → summer → envelope detector → ADC
   │
   ├── DAC → digital pot / varactor / phase shifter control
   │
   └── mux → memristor/emulator/crossbar → detector → ADC
```

### Recommended I/O port map

Use the project’s existing `memristor_interface.asm` idea, but make it more general.

| Port | Name | Direction | Function |
|---:|---|---|---|
| `10h` | `MUX_PORT` | OUT | select channel, row, column, experiment path |
| `11h` | `WRITE_PORT` / `DAC_PORT` | OUT | write DAC value, pulse value, phase value |
| `12h` | `ADC_PORT` | IN | read ADC result, detector level, memristor voltage |
| `13h` | `CTRL_PORT` | OUT | oscillator enable, trigger, mode bits |
| `14h` | `AMP_PORT` | OUT | amplitude control / second DAC latch |
| `15h` | `FREQ_PORT` | OUT | frequency selection / DDS command |
| `16h` | `ENV_ADC_PORT` | IN | envelope detector / filtered channel read |
| `17h` | `STATUS_PORT` | IN | comparator, busy flag, jumper detect, optional flags |

### Simple decoding

For a beginner kit, decoding `10h–17h` may be mirrored across other ports. That is acceptable for experiments if documented.

Minimal decode:

```text
/IORQ + /WR + A0‑A2 → write chip selects
/IORQ + /RD + A0‑A2 → read chip selects
```

Better decode:

```text
A7..A3 compare to 00010b  → only port range 10h–17h active
A2..A0 select one of eight internal registers
```

Suggested ICs:

- 74HC138 or 74LS138 for 3‑to‑8 decode
- 74HC688 for tight address compare
- 74HC245 for data bus buffering
- 74HC573 / 74HC574 for output latches
- 74HC244 for input buffering

---

## 8. Patch Bay Philosophy

The patch bay is the heart of the kit.

Every important signal should have a named patch point:

| Patch label | Meaning |
|---|---|
| `OSC_A` | oscillator A output |
| `OSC_B` | oscillator B output |
| `SINE_A` | sine output |
| `SQ_A` | square output |
| `PHASE_IN` | phase shifter input |
| `PHASE_OUT` | phase shifter output |
| `SUM_A` | summer input A |
| `SUM_B` | summer input B |
| `SUM_OUT` | mixed/interference output |
| `ENV_OUT` | envelope detector output |
| `ADC_IN` | ADC input |
| `DAC_OUT` | DAC voltage output |
| `MEM_A` | memristor terminal A |
| `MEM_B` | memristor terminal B |
| `X_SCOPE` | oscilloscope X output |
| `Y_SCOPE` | oscilloscope Y output |
| `SPEAKER` | audio output |
| `LED_BAR` | bargraph input |
| `VREF` | mid‑supply reference, usually 2.5 V |
| `GND` | ground |

### Example jumper instruction style

Each experiment card should use simple wiring instructions:

```text
Experiment 04 — Draw a circle
1. Patch OSC_A → X_SCOPE
2. Patch OSC_A → PHASE_IN
3. Patch PHASE_OUT → Y_SCOPE
4. Set PHASE knob near 90°
5. Connect oscilloscope in X‑Y mode
6. Adjust until the line becomes an ellipse/circle
```

That is the Maxitronix idea: fixed components, patch wires, clear recipe, fun result.

---

## 9. Functional Blocks

## 9.1 Power Block

Purpose: safe supply and reference voltages.

### Include

- +5 V digital rail
- GND rail
- analog rail input: 9–12 V DC optional
- optional ±5 V or ±9 V charge pump / DC‑DC converter
- virtual ground / reference at 2.5 V for single‑supply op‑amp work
- power LEDs
- resettable fuse
- reverse polarity protection
- decoupling capacitors near every IC

### Patch points

- `+5V`
- `GND`
- `VREF`
- `+ANA`
- `-ANA`

### Design note

For a beginner kit, many analog circuits can run from single 5 V with signals biased around `VREF = 2.5 V`. That avoids dangerous or confusing negative rails.

---

## 9.2 TEC‑1 / Z80 Interface Block

Purpose: allow the TEC‑1 to control experiments by I/O ports.

### Include

- TEC‑1 expansion connector or adapter header
- data bus buffer
- address decode
- output latches
- input buffer
- mode jumpers
- LEDs for `/IORQ`, `/RD`, `/WR`, selected port

### Patchable outputs

- `D0..D7_LED`
- `PORT10_SEL`
- `PORT11_SEL`
- `PORT12_SEL`
- `WR_PULSE`
- `RD_PULSE`

### Why this is fun

Users can type a few bytes into the TEC‑1 and physically see the Z80 talking to the outside world.

---

## 9.3 Oscillator Block

Purpose: make the signals used for Lissajous, sound, clocks, and experiments.

### Include three levels

1. **Simple 555 oscillator**
   - square wave
   - beginner friendly
   - speaker output

2. **Wien bridge / op‑amp sine oscillator**
   - cleaner Lissajous figures
   - 500 Hz – 5 kHz target

3. **Optional DDS / Arduino / AD9850 header**
   - stable programmable frequency
   - good for advanced phase experiments

### Controls

- frequency knob
- amplitude knob
- waveform select jumper

### Patch points

- `OSC_A`
- `OSC_B`
- `SINE_A`
- `SINE_B`
- `SQ_A`
- `SQ_B`
- `CLK_OUT`

---

## 9.4 Phase Shifter Block

Purpose: turn phase into a programmable “weight”.

### Include

- manual all‑pass filter
- socket for digital potentiometer module
- varactor phase shifter footprint
- cascade jumper for two stages

### First stage

Use an op‑amp all‑pass filter:

```text
Vin ──┬── R ──┐
      │       │
      C       │
      │       │
     VREF    op‑amp → Vout
```

The important idea:

```text
same amplitude, different timing
```

### Patch points

- `PHASE_IN`
- `PHASE_OUT1`
- `PHASE_OUT2`
- `PHASE_CTRL`
- `DIGIPOT_CS`
- `DIGIPOT_WIPER`

### Beginner experiment

Patch oscillator to phase input, unshifted signal to oscilloscope X, shifted signal to oscilloscope Y, then turn the knob and watch a line become an ellipse.

---

## 9.5 Interference / Neuron Block

Purpose: combine waves so that phase differences produce a result.

### Include

- op‑amp summer
- inverting/non‑inverting input options
- gain trim
- envelope detector
- comparator with threshold knob
- LED labelled `FIRED`

### Patch points

- `SUM_A`
- `SUM_B`
- `SUM_C`
- `SUM_OUT`
- `ENV_OUT`
- `THRESH`
- `FIRED_OUT`
- `ADC_IN`

### Educational meaning

This block demonstrates:

- constructive interference = bigger signal
- destructive interference = smaller signal
- threshold = neuron fires / does not fire

---

## 9.6 ADC / DAC Block

Purpose: convert between Z80 numbers and analog voltages.

### Include

- ADC input protection
- 8‑bit ADC option: ADC0804 style
- SPI/I2C ADC option via Arduino bridge if desired
- DAC0808 or MCP4725 DAC option
- R‑2R ladder fallback for cheap kit
- LEDs for ADC/DAC values

### Patch points

- `DAC_OUT`
- `ADC_IN`
- `ADC_READY`
- `ADC_DATA`
- `VREF_ADC`

### Basic idea

The TEC‑1 can output a number like `80h`, which becomes a voltage. The board uses that voltage to control phase, amplitude, or a memristor programming pulse. Then the board converts the result back into a number the TEC‑1 can read.

---

## 9.7 Memristor / Emulator Bay

Purpose: provide a safe place to compare a real experimental cell with stable substitutes.

### Include three plug‑in options

1. **Fixed resistor cartridge**
   - good for first tests
   - values: 1 k, 4.7 k, 10 k, 22 k, 47 k, 100 k

2. **Digital potentiometer emulator**
   - acts like programmable resistance
   - stable and repeatable

3. **Real memristor carrier**
   - copper pad + experimental material
   - current limited
   - removable

### Protection

Every path to the memristor bay should include:

- series resistor
- clamp diodes
- current‑limit jumper
- maximum pulse duration control

### Patch points

- `MEM_A`
- `MEM_B`
- `MEM_READ`
- `MEM_WRITE`
- `MEM_LIMITED`
- `MEM_SCOPE`

---

## 9.8 4×4 Crossbar Block

Purpose: show the idea of weights in rows and columns.

### Include

- 4 row lines
- 4 column lines
- sockets for resistor/emulator/memristor cells
- row/column mux
- LEDs showing selected row/column
- test points on every row and column

### Crossbar view

```text
        C0    C1    C2    C3
      ┌────┬────┬────┬────┐
R0 ───┤ W00│ W01│ W02│ W03│
R1 ───┤ W10│ W11│ W12│ W13│
R2 ───┤ W20│ W21│ W22│ W23│
R3 ───┤ W30│ W31│ W32│ W33│
      └────┴────┴────┴────┘
```

### Experiments

- read one cell
- write one emulator value
- scan all 16 cells
- make a memory pattern
- create a 2×2 matrix multiply demo
- make an XOR‑like phase interference demo

---

## 9.9 Output Block

Purpose: make results visible.

### Include

- 8 LEDs for data bus / ADC value
- LED bargraph
- piezo speaker
- comparator LED
- scope X/Y outputs
- optional 7‑segment display interface

### Patch points

- `LED_BAR_IN`
- `SPEAKER_IN`
- `X_SCOPE`
- `Y_SCOPE`
- `LOGIC_OUT`

---

## 10. Recommended Silkscreen Labels

The silkscreen should be extremely clear. Treat it like an instrument panel.

### Big printed labels

- `TEC‑1 BUS`
- `Z80 PORTS 10h–17h`
- `OSCILLATORS`
- `PHASE = WEIGHT`
- `INTERFERENCE = COMPUTATION`
- `ADC READ`
- `DAC WRITE`
- `MEMRISTOR / EMULATOR`
- `4×4 CROSSBAR`
- `X‑Y SCOPE OUTPUT`

### Printed warning labels

- `LOW VOLTAGE ONLY`
- `NO MAINS`
- `CURRENT LIMITED MEMRISTOR AREA`
- `CHECK JUMPER BEFORE RUN`
- `USE VREF FOR SINGLE‑SUPPLY ANALOG`

---

## 11. How the Project Files Map to This Kit

| Source file | Use in Experimenter 1 |
|---|---|
| `README.md` | main project theory and roadmap |
| `README-old.md` | raw notes and extra background |
| `LAB.md` | basis for ordered lab sequence |
| `Experimenter_Deck.md` | first version of the experimenter deck idea |
| `memristor_interface.asm` | Z80 port map and routines for memristor/crossbar control |
| `simple_read_example.asm` | minimal ADC read idea |
| `1.z80` | simple read‑voltage machine‑code concept |
| `test_1.md` | pulse driver / MINT style notes |
| `lissajous_logic_gates.m` | logic gate phase experiments |
| `lissajous_neural_network.m` | neural / XOR demonstration |
| `lissajous_hardware_design.m` | FDM / multiplexing experiments |
| `lissajous_hardware_design.md` | hardware scaling paths |
| `memristor_vs_lissajous.m` | memristor/Lissajous equivalence demonstration |
| `photonic-neural-networks/` | optional future light/fibre experiments |

---

## 12. Experiment Cards

This is the most important part for selling the kit. The board is hardware; the cards are the experience.

Each card should have:

1. Experiment number
2. Name
3. Goal
4. Jumper list
5. Knob settings
6. TEC‑1 code bytes if needed
7. What to observe
8. “Try this next” variation

---

# 13. Core Experiment Sequence

## Experiment 01 — Power and LED Rail Test

### Goal

Verify power rails and learn the board layout.

### Jumpers

```text
+5V → LED_BAR_IN through current limit path
GND → GND
```

### Observe

Power LED on. One LED bar segment lights.

### Try next

Move jumper to different LEDs.

---

## Experiment 02 — First TEC‑1 OUT Instruction

### Goal

Use the TEC‑1 to write a byte to the board.

### Jumper setup

```text
PORT10_LATCH → LED_BAR_IN
```

### Z80 assembly

```asm
LD A,55h
OUT (10h),A
HALT
```

### Hex bytes at `0800h`

```text
Address  Bytes
0800     3E 55
0802     D3 10
0804     76
```

### What happens

The board latches `55h` on port `10h`. The LED pattern should show alternating bits.

### Try next

Change `55` to `AA`, `0F`, `F0`, or `FF`.

---

## Experiment 03 — Read an ADC Value

### Goal

Turn a knob and let the TEC‑1 read the voltage.

### Jumper setup

```text
POT_WIPER → ADC_IN
ADC_DATA  → Z80 DATA BUS through ADC block
```

### Z80 assembly

```asm
LD A,01h
OUT (10h),A
LD B,0FFh
DELAY: DJNZ DELAY
IN A,(12h)
LD (0900h),A
XOR A
OUT (10h),A
HALT
```

### Hex bytes at `0800h`

```text
0800  3E 01 D3 10 06 FF 10 FE
0808  DB 12 32 00 09 AF D3 10
0810  76
```

### What happens

The TEC‑1 reads the ADC at port `12h` and stores the result at memory address `0900h`.

### Try next

Turn the pot and run again. The byte at `0900h` should change.

---

## Experiment 04 — Make a Tone

### Goal

Use the oscillator block as a sound source.

### Jumpers

```text
SQ_A → SPEAKER_IN
```

### Controls

Turn frequency knob.

### Observe

The speaker changes pitch.

### Try next

Patch `DAC_OUT → FREQ_CTRL` if the board has voltage‑controlled frequency.

---

## Experiment 05 — Draw a Lissajous Line

### Goal

Use oscilloscope X‑Y mode to see two related signals.

### Jumpers

```text
SINE_A → X_SCOPE
SINE_A → Y_SCOPE
```

### Scope setup

- X‑Y mode
- AC coupling optional
- start around 1 kHz

### Observe

You should see a diagonal line because X and Y are in phase.

---

## Experiment 06 — Turn the Line into an Ellipse

### Goal

See phase shift visually.

### Jumpers

```text
SINE_A    → X_SCOPE
SINE_A    → PHASE_IN
PHASE_OUT → Y_SCOPE
```

### Controls

Turn the phase knob.

### Observe

The line changes into an ellipse. Around 90 degrees it becomes more circle‑like.

### Meaning

This is the first visible proof of phase as an information carrier.

---

## Experiment 07 — Phase as a Weight

### Goal

Use the phase shifter as a controllable neural weight.

### Jumpers

```text
SINE_A    → SUM_A
SINE_A    → PHASE_IN
PHASE_OUT → SUM_B
SUM_OUT   → ENV_IN
ENV_OUT   → LED_BAR_IN
```

### Observe

As phase changes, the summed signal gets bigger or smaller. The LED bar changes.

### Meaning

Phase controls constructive or destructive interference.

---

## Experiment 08 — Z80 Sets a Phase Value

### Goal

Let the TEC‑1 set a DAC value that controls phase.

### Jumpers

```text
DAC_OUT → PHASE_CTRL
PHASE_OUT → Y_SCOPE
SINE_A → X_SCOPE
```

### Z80 assembly

```asm
LD A,80h
OUT (11h),A
HALT
```

### Hex bytes at `0800h`

```text
0800  3E 80 D3 11 76
```

### What happens

The board writes `80h` to the DAC/phase port. This should move the phase control toward mid‑scale.

### Try next

Change `80` to `20`, `40`, `C0`, and `F0`.

---

## Experiment 09 — Interference Gate: YES/NO Threshold

### Goal

Use analog interference plus a comparator as a simple logic decision.

### Jumpers

```text
SINE_A    → SUM_A
PHASE_OUT → SUM_B
SUM_OUT   → ENV_IN
ENV_OUT   → COMP_IN
COMP_OUT  → FIRED_LED
```

### Controls

- phase knob
- threshold knob

### Observe

The `FIRED` LED turns on only when the summed wave is strong enough.

### Meaning

This is a one‑neuron classifier.

---

## Experiment 10 — Read the Neuron Output with TEC‑1

### Goal

Let Z80 read the result of the analog computation.

### Jumpers

```text
ENV_OUT → ADC_IN
```

### Program

Use Experiment 03 ADC read program.

### Observe

The byte at `0900h` rises and falls as the phase changes.

---

## Experiment 11 — Continuous ADC to LED Port

### Goal

Make the TEC‑1 continuously copy ADC input to an output latch.

### Jumper setup

```text
POT_WIPER or ENV_OUT → ADC_IN
PORT00/LED_LATCH     → LED_BAR_IN
```

### Z80 assembly

```asm
LOOP:
    IN A,(12h)
    OUT (00h),A
    JP LOOP
```

### Hex bytes at `0800h`

```text
0800  DB 12 D3 00 C3 00 08
```

### Note

Only use port `00h` if your TEC‑1 / board display latch is safe there. Otherwise replace `00` with your board’s LED output port.

---

## Experiment 12 — Memristor Emulator as a Variable Resistor

### Goal

Use a stable digital pot / emulator before using real experimental memristors.

### Jumpers

```text
DAC_OUT     → EMU_CTRL
EMU_A       → MEM_A
EMU_B       → MEM_B
MEM_READ    → ADC_IN
```

### Program

Use Experiment 08 to set DAC value, then Experiment 03 to read it back.

### Observe

Changing the DAC value changes the measured “resistance” or output voltage.

---

## Experiment 13 — Select a Crossbar Cell

### Goal

Use port `10h` to select one row/column.

### Cell encoding

Recommended simple encoding:

```text
A register low nibble  = row 0–3
A register high nibble = column 0–3
```

Example:

```text
row 2, column 1 = 12h
row 3, column 2 = 23h
```

### Z80 assembly

```asm
LD A,12h
OUT (10h),A
HALT
```

### Hex bytes

```text
0800  3E 12 D3 10 76
```

### Observe

Row 2 and column 1 LEDs should indicate the selected cell.

---

## Experiment 14 — Pulse a Selected Cell / Emulator

### Goal

Send a write pulse to the selected cell.

### Z80 assembly

```asm
LD A,12h
OUT (10h),A      ; select row 2, column 1
LD A,88h
OUT (11h),A      ; write pulse / DAC command
HALT
```

### Hex bytes

```text
0800  3E 12 D3 10 3E 88 D3 11 76
```

### Meaning of `88h`

Example only. On the final board, define bits clearly:

```text
bit 7 = trigger
bits 6..4 = duration
bit 3 = mode
bit 2..1 = range
bit 0 = polarity
```

---

## Experiment 15 — Real Memristor Caution Lab

### Goal

Test a real experimental cell safely.

### Required

- current limit jumper set to highest resistance
- low voltage only
- short pulse duration
- eye protection and ventilation if fabricating cells

### Jumpers

```text
MEM_CARRIER_A → MEM_A
MEM_CARRIER_B → MEM_B
MEM_READ      → ADC_IN
```

### Observe

Read value before and after very small SET/RESET pulses. Look for state change. Do not expect every homemade cell to behave well.

---

## Experiment 16 — 2×2 Matrix Toy Computer

### Goal

Demonstrate matrix weighting using four cells.

### Build

Use only cells:

```text
W00 W01
W10 W11
```

Use resistor cartridges first.

### Idea

Rows are inputs. Columns are outputs. Lower resistance means stronger weight.

### What to observe

Changing one cell changes the output sum.

---

## Experiment 17 — XOR by Interference

### Goal

Demonstrate why phase computing can represent non‑simple logic.

### Setup

Use two signal paths:

```text
Input A path → SUM_A
Input B path → PHASE_SHIFTER → SUM_B
SUM_OUT → ENV → COMP → FIRED
```

### Try

Patch different phase settings for four cases:

| A | B | Desired XOR |
|---:|---:|---:|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

### Simplification

In the kit version, use switches for A/B and pre‑marked phase knob regions instead of demanding perfect mathematical XOR at first.

---

## Experiment 18 — Frequency Multiplexing Demo

### Goal

Show multiple signals sharing one wire.

### Jumpers

```text
OSC_A 1 kHz → SUM_A
OSC_B 2 kHz → SUM_B
SUM_OUT     → FILTER_BANK_IN
FILTER1_OUT → LED1
FILTER2_OUT → LED2
```

### Observe

Two signals exist together but can be separated by filters.

### Project connection

This connects to `lissajous_hardware_design.m`, where multiple carrier frequencies act like separate parallel neurons.

---

## Experiment 19 — Burst Coding

### Goal

Make pulses carry importance.

### Jumpers

```text
CLK_OUT → BURST_IN
BURST_OUT → LED / SPEAKER / SUM input
```

### Observe

A burst sounds and looks different from a single pulse.

### Meaning

A burst can mean “stronger confidence” or “important event”.

---

## Experiment 20 — Z80 Auto‑Scan of 16 Cells

### Goal

Have the Z80 step through the whole crossbar.

### Pseudocode

```asm
for cell = 0 to 15:
    OUT (10h), cell
    wait
    IN A,(12h)
    store A to memory table
```

### Result memory

Store readings at:

```text
0900h–090Fh
```

### Manual first version

Enter a short version that scans only 4 cells. Expand later in the software package.

---

## Experiment 21 — Draw a Memory Map with LEDs

### Goal

Show crossbar values as a light pattern.

### Setup

Use resistor/emulator cells.

### Observe

Each cell reading becomes one LED brightness or bargraph value.

### Fun variation

Make a 4×4 smiley or letter pattern using resistor values.

---

## Experiment 22 — Audio as Analog Computation

### Goal

Listen to phase and interference.

### Jumpers

```text
SUM_OUT → SPEAKER_IN
```

### Observe

As phase moves, sound changes in volume/tone.

### Meaning

Your ear is detecting interference.

---

## Experiment 23 — Optical Doorway

### Goal

Show that light can carry the same ideas.

### Jumper setup

```text
OSC_A → LED_DRIVER
PHOTODIODE_OUT → ADC_IN
```

### Observe

Interrupting light changes ADC reading.

### Advanced

Add a fibre path or piezo stretcher later.

---

## Experiment 24 — TEC‑1 as Training Controller

### Goal

Use the Z80 to try a list of phase values and remember the best one.

### Simplified method

1. Z80 writes phase value.
2. Board produces interference result.
3. Z80 reads ADC.
4. If ADC is higher than previous best, save that phase.

### This is not full AI yet

But it is the seed of training.

---

## Experiment 25 — Mini Phase Neural Demo

### Goal

Combine everything:

```text
TEC‑1 writes phase → oscillator sends wave → phase block shifts wave → summer interferes → envelope detector produces answer → ADC sends answer back to TEC‑1
```

### Result

A complete closed loop:

```text
number → voltage → phase → wave interference → voltage → number
```

That is the core of this project.

---

# 14. TEC‑1 Hex Keypad Code Cards

These cards assume:

```text
Start address: 0800h
MUX/control port: 10h
DAC/write port: 11h
ADC/read port: 12h
Result memory: 0900h
```

Change the port numbers if your actual TEC‑1 hardware uses different I/O decoding.

## Code Card A — Output `55h` to Port `10h`

```asm
LD A,55h
OUT (10h),A
HALT
```

```text
0800: 3E 55 D3 10 76
```

## Code Card B — Output `AAh` to Port `10h`

```asm
LD A,AAh
OUT (10h),A
HALT
```

```text
0800: 3E AA D3 10 76
```

## Code Card C — Read ADC Once into `0900h`

```asm
LD A,01h
OUT (10h),A
LD B,0FFh
DJNZ $
IN A,(12h)
LD (0900h),A
XOR A
OUT (10h),A
HALT
```

```text
0800: 3E 01 D3 10 06 FF 10 FE
0808: DB 12 32 00 09 AF D3 10
0810: 76
```

## Code Card D — Set Mid Phase / DAC Value

```asm
LD A,80h
OUT (11h),A
HALT
```

```text
0800: 3E 80 D3 11 76
```

## Code Card E — Continuous ADC to LED Output

```asm
LOOP:
IN A,(12h)
OUT (00h),A
JP LOOP
```

```text
0800: DB 12 D3 00 C3 00 08
```

Replace `00h` with the actual LED output port if required.

## Code Card F — Select Crossbar Cell `row 2, column 1`

```asm
LD A,12h
OUT (10h),A
HALT
```

```text
0800: 3E 12 D3 10 76
```

## Code Card G — Select Cell and Send Write Pulse

```asm
LD A,12h
OUT (10h),A
LD A,88h
OUT (11h),A
HALT
```

```text
0800: 3E 12 D3 10 3E 88 D3 11 76
```

---

# 15. MINT‑Style Hooks

The project can later expose simple MINT words. Exact syntax depends on your TEC‑1 MINT build, but the idea is:

```text
10 CONSTANT MUX
11 CONSTANT DAC
12 CONSTANT ADC

: CELL  MUX OUT ;       \ select cell/channel
: PHASE DAC OUT ;       \ write phase/DAC value
: READ  ADC IN ;        \ read ADC byte
```

Example use:

```text
12 CELL
80 PHASE
READ .
```

The kit manual should keep Z80 machine code as the guaranteed path, then add MINT as a bonus layer once the user’s firmware is known.

---

# 16. Suggested BOM by Block

This is a design BOM, not a final purchasing BOM.

## Digital interface

| Part | Qty | Notes |
|---|---:|---|
| 74HC245 / 74HCT245 | 1–2 | data bus buffer |
| 74HC573 / 74HCT573 | 2–4 | output latches |
| 74HC244 / 74HCT244 | 1 | input buffer |
| 74HC138 / 74HCT138 | 1–2 | port decode |
| 74HC688 | 1 | optional tight port compare |
| 74HC4051 | 2–4 | analog mux row/column/channel |
| LEDs + resistors | many | visible bus/debug state |

## Analog

| Part | Qty | Notes |
|---|---:|---|
| NE555 / TLC555 | 1–2 | simple oscillators |
| TL072 / TL074 | 2–4 | sine, all‑pass, summing |
| LM358 / MCP6002 | 2–4 | single‑supply op‑amp options |
| diodes | many | protection, envelope detector |
| pots/trimmers | many | frequency, phase, threshold |
| capacitors/resistors | many | timing/filter networks |

## ADC/DAC

| Part | Qty | Notes |
|---|---:|---|
| ADC0804 | 1 | simple 8‑bit parallel ADC option |
| DAC0808 | 1 | classic DAC option |
| MCP4725 module | optional | easier I2C DAC via bridge |
| R‑2R resistor ladder | optional | cheap educational DAC |

## Memristor / emulator

| Part | Qty | Notes |
|---|---:|---|
| resistor plug‑in cards | many | stable fake weights |
| MCP4131 / MCP41010 | 1–4 | digital pot emulator |
| copper pad carrier | optional | real memristor experiments |
| current limit resistors | many | mandatory |
| 2‑pin removable terminals | many | swap cells safely |

## Mechanical / kit parts

| Part | Qty | Notes |
|---|---:|---|
| 250 × 200 mm PCB | 1 | main board |
| jumper wires | 30–80 | key selling feature |
| knobs | 4–8 | tactile and fun |
| speaker / piezo | 1 | audio feedback |
| acrylic cover | optional | classroom safety |
| printed cards | 25+ | experiment manual |

---

# 17. Suggested Board Revisions

## Revision A — Proof of Concept

- 2‑layer board
- only one oscillator
- one phase shifter
- one summer
- one ADC
- one DAC / R‑2R ladder
- no real memristor chemistry
- 8–12 experiments

## Revision B — Sellable Base Kit

- full 250 × 200 mm board
- better silkscreen
- patch bay
- 4×4 emulator crossbar
- 25 experiment cards
- stable Z80 examples

## Revision C — Deluxe Kit

- digital pot phase controls
- DDS socket
- photonic header
- real memristor carrier cards
- classroom manual

---

# 18. Manual / Packaging Structure

## Box contents

- Experimenter 1 PCB
- component pack or assembled board depending on product level
- jumper wires
- TEC‑1 adapter cable
- printed experiment cards
- safety sheet
- quick start sheet

## Manual sections

1. What this kit is
2. Safety
3. Board map
4. TEC‑1 connection
5. How to enter code on hex keypad
6. First five experiments
7. Oscillator labs
8. Lissajous labs
9. Phase shifter labs
10. ADC/DAC labs
11. Memristor emulator labs
12. Crossbar labs
13. Advanced memristor labs
14. Troubleshooting
15. Full port map
16. Full code listing

---

# 19. How to Make It Feel Fun

Add physical feedback everywhere:

- LEDs flash when ports are selected.
- Speaker clicks when a pulse fires.
- LED bar shows analog level.
- Scope outputs show beautiful Lissajous patterns.
- Crossbar LEDs show selected row/column.
- Comparator LED says `FIRED` like a neuron.
- Printed cards use names like:
  - “Make a line dance”
  - “Turn timing into memory”
  - “Teach a wave to say YES”
  - “Build a one‑neuron brain”
  - “Make the Z80 train a phase”

The emotional hook is important: the user should feel they are controlling invisible waves with an old Z80.

---

# 20. Troubleshooting Table

| Symptom | Likely cause | Fix |
|---|---|---|
| No LEDs | no 5 V, wrong jumper, fuse open | check power rail |
| Z80 crashes | bus loading, wrong buffer direction | isolate board, test port decode only |
| OUT does nothing | wrong port decode | check `/IORQ`, `/WR`, A0–A2 LEDs |
| ADC always 0 | no signal at ADC input, wrong VREF | patch pot to ADC_IN first |
| ADC always 255 | input overrange | check clamp/protection, lower gain |
| Lissajous is just a dot | no oscillator or wrong scope mode | use X‑Y mode, check signal amplitude |
| Lissajous is a line only | phase shift not connected | patch through PHASE block |
| Phase knob does nothing | wrong capacitor/pot path | check PHASE_IN/OUT and VREF bias |
| Memristor never changes | current too low or bad cell | test with emulator first |
| Memristor becomes short | pulse too strong | increase series resistor, reduce pulse |
| Noise everywhere | no decoupling, long wires | add caps, shorten jumpers, use VREF correctly |

---

# 21. Manufacturing Notes

## PCB design notes

- Use wide power traces.
- Put decoupling capacitors at every IC.
- Separate analog and digital grounds but join at one point near power input.
- Keep oscillator and high‑impedance analog nodes away from data bus traces.
- Put guard rings or keep‑outs around very high impedance memristor read nodes.
- Use test pads for every important signal.
- Make silkscreen large enough to read while patching.
- Put port map on the board itself.

## Kit assembly options

### Through‑hole kit

Best for hobbyists and education. Larger board, easier repairs.

### Pre‑assembled SMD + through‑hole controls

Best for selling to beginners. The user patches and experiments but does not need to solder ICs.

### Hybrid

Pre‑assemble bus interface and power. Let user solder optional experiment sections.

---

# 22. Compliance / Selling Checklist

Before selling as a product:

- Check Australian product safety obligations.
- Avoid button/coin batteries unless you fully comply with mandatory battery safety and labelling standards.
- Avoid mains power entirely.
- Use an approved external plugpack if needed.
- Check EMC / RCM obligations for electronic products.
- Provide clear age recommendation.
- Provide warning labels for chemicals, heat, and experimental materials.
- Provide replacement/refund and safety recall process.
- Keep build records, BOM, revision history, and test procedure.

This document is a technical design plan, not legal certification.

---

# 23. Minimum Viable Product

The fastest useful version is:

1. TEC‑1 port decode for `10h`, `11h`, `12h`.
2. LED output latch on `10h`.
3. DAC or R‑2R ladder on `11h`.
4. ADC on `12h`.
5. One oscillator.
6. One all‑pass phase shifter.
7. One op‑amp summer.
8. One envelope detector.
9. One emulator cell.
10. 10 experiment cards.

That proves the whole concept.

Do not start with the full 4×4 real memristor array. Start with one stable channel and make it fun.

---

# 24. Final Recommended Product Positioning

Call the first product:

> **Experimenter 1: Z80 Wave, Phase & Memory Lab**

Subtitle:

> A patch‑wire add‑on board for TEC‑1 experiments in oscillators, Lissajous figures, phase‑coded logic, ADC/DAC control, and memristor‑style memory.

Target buyers:

- TEC‑1 owners
- retrocomputer builders
- electronics teachers
- analog computing fans
- Z80 learners
- people interested in neuromorphic / memristor ideas

Main promise:

> Type bytes into an old Z80 and watch waves compute.

---

# 25. Next Engineering Step

The next document should be:

```text
experimenter1_schematic_plan.md
```

It should convert this concept into actual KiCad sheets:

1. Power
2. TEC‑1 bus interface
3. Port decode
4. Output latches
5. Input ADC
6. DAC / R‑2R
7. Oscillator
8. Phase shifter
9. Summer / detector
10. Memristor/emulator bay
11. 4×4 crossbar
12. Patch bay connectors

After that, create:

```text
experimenter1_experiment_cards.md
experimenter1_bom.csv
experimenter1_port_test.z80
experimenter1_kicad_notes.md
```

---

## End

