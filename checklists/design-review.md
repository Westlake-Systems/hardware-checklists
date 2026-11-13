# Schematic and layout review checklist

What to check in a schematic and board layout before you order boards: power, parts, clocks, RF, layout, EMC, thermal, DFM, test access, and release.

Interactive and printable version: [https://westlakesys.com/tools/checklists/design-review/](https://westlakesys.com/tools/checklists/design-review/)

What to look at when reviewing a schematic and board layout, for teams running their own reviews. Work through it once at the schematic stage and again when layout is done, before the board order goes in.

Not every item applies to every board, so skip what does not fit, but decide that deliberately. Record each finding with a decision: fixed, accepted, or deferred, and why.

## 1. Requirements and architecture

- [ ] **1.1** Written requirements cover function, environment, power source and runtime, target markets, cost, and volume.
  Without them, a review can only check that the circuit agrees with itself.
- [ ] **1.2** The block diagram and power tree are current and match the schematic.
- [ ] **1.3** Processor speed, RAM, flash, and timing have headroom beyond what the first firmware needs.
  Firmware grows, and field updates need room to land.
- [ ] **1.4** Single points of failure are known: sole-source parts, a single clock, a connector that carries everything.
- [ ] **1.5** Critical parts are active, in stock, and have an identified alternate, judged against how long the product must be built.
  A part marked not recommended for new designs is a finding now, not later.

## 2. Power

- [ ] **2.1** Every rail has a defined source, worst-case load, and place in the power-up and power-down sequence.
- [ ] **2.2** Worst-case current includes startup, inrush, radio transmit bursts, and motor stall, not just the average.
- [ ] **2.3** Each regulator matches its datasheet and is stable with the parts chosen: capacitor ESR and effective capacitance, inductor saturation current, feedback, compensation, and soft start.
  Some linear regulators need a minimum ESR and can oscillate with low-ESR ceramics.
- [ ] **2.4** Ceramic capacitor values are derated for DC bias, temperature, and tolerance.
  A small-case capacitor can lose most of its capacitance at its working voltage.
- [ ] **2.5** Every part is within its voltage, current, and power ratings at worst case, across the full temperature range.
- [ ] **2.6** Absolute maximum ratings hold on every pin during power-up, power-down, and hot-plug, and no I/O pin drives a chip whose rail can be off.
  Current through input protection diodes can half-power a chip and leave it in an undefined state.
- [ ] **2.7** Brown-out and reset thresholds give a clean reset on a sagging supply, and a pulled cable cannot corrupt a write in progress.
- [ ] **2.8** Input protection fits how the product is powered: reverse polarity, overvoltage, transients, and inrush.
- [ ] **2.9** For battery products, the quiescent current of every rail and the sleep current fit the power budget.
- [ ] **2.10** A rechargeable cell's charge voltage, current, and temperature limits are set for that cell, with protection against overcharge, overdischarge, and short circuit.
  Charging outside the temperature range the cell allows is a common cause of damaged cells.
- [ ] **2.11** The enable chain has no loop: every enable comes from a signal that is valid in every state, and the processor's own supply starts without any setup from the processor.
  A regulator that needs I2C setup before it starts cannot power the processor that would set it up.
- [ ] **2.12** At the lowest source voltage and full load, after every drop along the input path, each regulator's input stays above its dropout and undervoltage lockout, and the source can supply the current.
  Current rises as the voltage falls, and a load step that drops the input by more than the lockout hysteresis makes a low battery switch the rail off and on.
- [ ] **2.13** Where more than one source can power the product, such as USB, an adapter, a battery, or a debug probe, the sources are combined on purpose, and none can feed current back into another or into a host.
  An LDO whose output can sit above its input, unless it blocks reverse current itself, or a converter switched off with its output held up, needs reverse-current blocking.
- [ ] **2.14** An LC or ferrite filter ahead of a switching regulator is damped, so it cannot resonate with the regulator's negative input impedance.
  An undamped input filter can make an otherwise stable regulator oscillate.
- [ ] **2.15** Each regulator and load switch has a known response to overload and overheating, such as hiccup, latch, or foldback, the loads tolerate it, how a latched fault is cleared is defined, and the part stays inside its safe operating area while it retries.
  Safe operating area shrinks with temperature and pulse length, so a retry that is safe once can overheat a part when it repeats.
- [ ] **2.16** Tantalum capacitors are derated in voltage as their maker recommends and protected from surge current, and no polarized capacitor is reverse-biased in any power state.
  Manganese dioxide tantalum capacitors fail short and can burn, and surge and overvoltage are the usual cause.
- [ ] **2.17** A product that runs while it charges has a power path, or a charger the running load cannot confuse, so the battery still charges and the charge ends correctly.
  Without a power path, the load current looks like a battery that never fills, and the charger can time out or never finish.
- [ ] **2.18** Each switching regulator meets its minimum on-time and off-time at the highest and lowest input voltage and the chosen switching frequency.
  A high input stepped down to a low output at a high frequency can need a pulse shorter than the part can make, so it skips pulses and the ripple grows.

## 3. Schematic and parts

- [ ] **3.1** Every symbol is checked pin by pin against the datasheet for the exact part number and package being bought.
- [ ] **3.2** Every power and ground pin is connected, including exposed pads and hidden or duplicate-named pins.
  Hidden power pins in library symbols can tie a pin to the wrong net without an ERC warning.
- [ ] **3.3** Decoupling capacitors are on every supply pin, with values the datasheet recommends.
- [ ] **3.4** No input is left floating: unused pins, enables, and address pins are tied or configured as the datasheet says.
- [ ] **3.5** Reset, boot, and strap pins have defined states during power-up, with pull resistors sized against internal pulls and other loads on the net.
  A strap read at the wrong level can boot the part into the wrong mode, and only sometimes.
- [ ] **3.6** Open-drain and I2C lines have one set of pull-ups per bus, sized for the bus capacitance and speed.
  Too weak and edges are slow; several sets in parallel can be too strong for the weakest driver.
- [ ] **3.7** Logic levels agree at both ends of every connection, with level shifting where they do not.
- [ ] **3.8** Dividers, references, and analog gain stages are calculated with component tolerances, and stay in range at the extremes.
- [ ] **3.9** The electrical rule check is clean, each remaining warning is explained, and net names are checked for accidental merges and splits.
  Two labels on one net, or a typo that splits a net, passes most electrical rule checks.
- [ ] **3.10** The errata for each complex part, such as a processor, FPGA, PHY, power management IC, or radio, are read for the silicon revision being bought, and every advisory that affects the board has a recorded decision.
  Errata can call for a pull-up, a series resistor, or a sequencing rule that the datasheet never mentions.
- [ ] **3.11** Every output that controls a load, such as a FET gate, a driver enable, a DAC, or an isolator, holds a safe state from power-up until firmware takes over, including any glitch the pin is known to have at power-up.
  DACs and isolators set their power-up and loss-of-supply states by part number or pin, and a gate with no pull-down floats until it is driven.
- [ ] **3.12** Strap, boot, and reset pins that reach a connector, button, or debug header cannot be pulled to the wrong level during reset by whatever is attached, including a button the enclosure presses.
  A button held down by a tight case keeps the board in reset or in its bootloader, and looks like a dead board.
- [ ] **3.13** Relays, solenoids, and motor coils have a flyback diode or clamp rated for the coil current, at the coil or at the connector when the coil is off the board.
  The turn-off spike can destroy the driver, and on a cable it also radiates.
- [ ] **3.14** Every amplifier and comparator input has a DC path for its bias current, and each amplifier is stable with its real load, such as a cable, an ADC input, or a large capacitor.
  Capacitance at the output can make a stage ring or oscillate in the product even though it looked fine on the bench; an isolation resistor usually fixes it.
- [ ] **3.15** Each ADC input settles to the needed accuracy within the acquisition time, and noise above half the sample rate is filtered before the converter.
  The small RC at the input that supplies the ADC's sampling charge is usually far too fast to count as the anti-aliasing filter.
- [ ] **3.16** Current-sense shunts give a usable signal at the smallest current to be measured and stay in range at the largest, with Kelvin connections taken from the shunt's own pads.
  Sensing from the copper that carries the current adds its resistance to the reading, so the result changes with layout and load.

## 4. Protection and connectors

- [ ] **4.1** Every exposed connector, button, and seam has ESD protection where the energy enters, with a planned path to ground or chassis.
- [ ] **4.2** Connector pinouts match the mating connector and cable, including pin 1.
  Pin numbering often mirrors between the board connector and the cable end.
- [ ] **4.3** Connectors are keyed, or the circuit survives a cable that is reversed, misaligned, or plugged in hot.
- [ ] **4.4** Connector current ratings cover the worst-case load, with enough ground pins for fast signals.
  Derate for pins carrying current side by side, and for temperature.
- [ ] **4.5** Outputs that power external devices have a fuse or current limit, and a defined behavior when shorted.
- [ ] **4.6** Every external connector pin survives, or a fuse opens first, at the highest voltage that a foreseeable wiring mistake or a short to a neighboring pin can put on it, whether the circuit behind it is on or off.
  A series resistor ahead of an input keeps the current through its protection diodes inside the datasheet limit, and a foreign supply on an output that is switched off can still feed back through its body diode.
- [ ] **4.7** Nothing crosses an isolation barrier except the parts listed as bridging it: no net, pour, mounting hole, test point ground, or cable shield.
  One screw or probe ground on the wrong side defeats the isolation without any warning in the schematic.
- [ ] **4.8** Connectors that look alike or take the same cable cannot be swapped without harm, or are clearly marked.
  Two identical headers side by side invite a swapped cable, which keying within each connector does not prevent.

## 5. Clocks and signals

- [ ] **5.1** Crystal load capacitors are calculated from the crystal load capacitance and the board stray capacitance.
  Frequency error and oscillator start-up margin both depend on it.
- [ ] **5.2** Clock tolerance, aging, and temperature drift fit the timing budget of every protocol that uses it.
  A UART tolerates a few percent of error; a radio often needs tens of parts per million.
- [ ] **5.3** Key clocks can be observed through a clock-output pin or test point, without probing a crystal.
- [ ] **5.4** Fast clock and data lines have series termination or footprints for it, and edges are no faster than they need to be.
  Drive-strength settings and series resistors both slow edges that would otherwise ring and radiate.
- [ ] **5.5** Controlled-impedance nets and differential pairs are marked in the schematic, with target impedance and polarity.
- [ ] **5.6** Sensitive analog inputs and references are filtered and kept away from noisy circuits.
- [ ] **5.7** Synchronous interfaces such as SPI and parallel memory have a worst-case setup and hold budget at the real clock rate, including the delay through any level shifter, isolator, or buffer.
  A read through an isolator pays its delay twice, once out and once back.
- [ ] **5.8** Signals that leave the board are checked at the real cable length for capacitance and edge rate, and bus cables such as RS-485 and CAN are terminated at the two ends of the trunk only, with a defined idle state.
  A node that carries its own terminator takes it away when it is unplugged.

## 6. RF and antenna

- [ ] **6.1** A radio module is placed exactly as its integration guide requires: antenna type, keep-outs, ground plane, and orientation.
  Changing these can bring back the radio testing the module was meant to save.
- [ ] **6.2** A chip-down radio copies the chip vendor's matching and filter network, with a separate adjustable network for the antenna.
- [ ] **6.3** RF traces are short, impedance-controlled, and run over solid ground with stitching vias along both sides.
- [ ] **6.4** The RF path has a switched test connector or pads for a coax pigtail, for conducted measurements.
- [ ] **6.5** The antenna is clear of metal, the battery, and the display, with the ground plane size it was designed for.
- [ ] **6.6** With more than one radio, antennas are separated and coexistence signals are wired.
- [ ] **6.7** Harmonics of clocks, switching regulators, and transmitters are checked against every receive band in the product.
  A harmonic that lands in a receive band raises the noise floor and cuts range.

## 7. Layout and stackup

- [ ] **7.1** Placement matches the mechanical drawing: outline, mounting holes, connectors, keep-outs, and height limits.
- [ ] **7.2** The stackup is agreed with the fab before routing, and impedance trace widths are calculated from it.
- [ ] **7.3** Every fast signal has a continuous reference plane, with no routing across splits or gaps.
  A gap forces the return current around it, and the loop it makes radiates.
- [ ] **7.4** Fast signals that change layers have a return via or stitching capacitor close to the transition.
- [ ] **7.5** Decoupling capacitors sit at the pins they serve, with short, wide connections and vias right at the pads.
- [ ] **7.6** Switching regulator layout follows the datasheet: a tight input loop, a small switch node, and feedback routed away from the inductor.
- [ ] **7.7** Crystals sit close to their chip, with short traces and no other signals routed underneath.
- [ ] **7.8** Trace widths and via counts are sized for current, with temperature rise checked on high-current paths.
- [ ] **7.9** Creepage and clearance meet the applicable safety standard wherever higher voltages are present.
- [ ] **7.10** The design rule check uses the fab's actual capabilities, and every waiver is explained.

## 8. EMC

- [ ] **8.1** Footprints are reserved for likely fixes: series resistors, cable filters, a shield can, and a ferrite on the power input.
  Unpopulated footprints cost almost nothing; adding them after a failed test means a respin.
- [ ] **8.2** Every cable that leaves the enclosure is filtered at its connector.
- [ ] **8.3** Cable shields, the enclosure, and circuit ground connect in a defined way.
- [ ] **8.4** Fast signals stay away from board edges, and ground stitching vias run around the perimeter.

## 9. Thermal

- [ ] **9.1** Dissipation is estimated for each part that runs warm, at maximum ambient and worst-case load.
- [ ] **9.2** Exposed pads are connected, have thermal vias, and have a windowed paste opening.
  A single large paste opening can float the part and leave the edge pins open.
- [ ] **9.3** Hot parts are kept away from crystals, batteries, electrolytic capacitors, and sensors.
- [ ] **9.4** The heat path works in the closed enclosure, not just on an open bench.
- [ ] **9.5** Junction temperatures from theta-JA are trusted only when the board resembles the datasheet's test board; otherwise the estimate uses this board's own copper, vias, and planes.
  Most of the heat leaves through the test board, so a smaller board or one with less copper runs hotter than theta-JA predicts.

## 10. DFM and assembly

- [ ] **10.1** Footprints match the datasheet's recommended land pattern for the exact package variant.
  Library footprints often differ from the recommendation in pad size, paste, or thermal pad.
- [ ] **10.2** Pin 1 and polarity marks on the silkscreen are still visible after the part is placed.
  A mark hidden under the part body cannot be checked at inspection.
- [ ] **10.3** Global fiducials are on the board or panel, with local fiducials near fine-pitch parts.
- [ ] **10.4** Spacing allows for placement, inspection, rework, and mating connectors and cables.
- [ ] **10.5** Vias in pads are filled and capped, or kept off pads so solder does not wick away.
- [ ] **10.6** Panel rails, tabs, or V-scores are clear of parts and edge connectors, and agreed with the assembler.
- [ ] **10.7** Ceramic capacitors and BGAs are kept away from board edges, break-off tabs, V-scores, mounting holes, and connectors that flex the board, or are turned to reduce the strain.
  A flex crack in a capacitor can pass test and turn into a short later.

## 11. Test and bring-up access

- [ ] **11.1** Every power rail, reset, and key signal has a test point, reachable by a fixture from one side.
  A fixture that probes both sides costs much more than one that probes one side.
- [ ] **11.2** Board sections can be powered and measured separately, using zero-ohm links or jumpers.
  A single total current tells you something is wrong, not what.
- [ ] **11.3** The programming and debug header is reachable in the enclosure, and can be locked on production units.
- [ ] **11.4** Firmware can read the board revision, from strap resistors or ID pins.
- [ ] **11.5** A serial log output or status LED is available to firmware from day one.
- [ ] **11.6** Firmware can be updated in the field, a failed update can be recovered, and boot pins can be overridden without rework.

## 12. Documentation and release

- [ ] **12.1** Schematic notes record assumptions, DNP parts, assembly options, and the reasons behind key values.
- [ ] **12.2** The board revision is on the silkscreen or in copper.
- [ ] **12.3** The schematic, layout, and BOM are at the same revision, and DNP parts agree across all three.

## Related reading

- [What I look for in a hardware design review](https://westlakesys.com/articles/design-review/)
- [Before your first board spin](https://westlakesys.com/articles/first-board-spin/)
- [What a complete manufacturing package includes](https://westlakesys.com/articles/manufacturing-package/)
- [Antenna and RF integration checklist](https://westlakesys.com/tools/checklists/antenna-integration/)
- [Crystal load capacitor calculator](https://westlakesys.com/tools/crystal-load-caps/)
- Next step: [First board bring-up checklist](board-bring-up.md)

---

From [Westlake Systems](https://westlakesys.com/). Licensed under [CC BY 4.0](../LICENSE): reuse and adapt freely, with credit and a link to the original page.
