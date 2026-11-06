# First board bring-up checklist

How to bring up a new board safely and learn the most from it: preparation, inspection, first power, clocks, debug, peripherals, RF, and power.

Interactive and printable version: [https://westlakesys.com/tools/checklists/board-bring-up/](https://westlakesys.com/tools/checklists/board-bring-up/)

A working list for the first power-up of a new board, for teams doing their own bring-up. The goal is to power the first board without damage, then learn as much as possible from this spin.

Do the first section before the boards arrive. After that, work in order and keep notes for each board as you go.

## 1. Before boards arrive

- [ ] **1.1** A written bring-up plan lists the order of steps, what working means for each, and the equipment each needs.
  Power first, then clocks and reset, then the processor, then each subsystem.
- [ ] **1.2** Equipment is on hand: current-limited bench supply, multimeter, a scope with enough bandwidth, a logic analyzer, and the probes and adapters to reach the board.
- [ ] **1.3** The debug probe and programming tools are proven on a development kit with the same processor.
- [ ] **1.4** Bring-up firmware is ready: a minimal image that blinks an LED, prints over serial, and tests each peripheral on its own.
- [ ] **1.5** Supply voltage and current limit are worked out for each input, with the limit just above the expected startup current.
  Too high and a short can burn a trace; too low and the board never starts.
- [ ] **1.6** Expected current and resistance to ground are noted for each rail, so an abnormal reading stands out.
- [ ] **1.7** A harness or breakout that reaches every interface is built.
- [ ] **1.8** A log is set up for each board serial number: measurements, issues, and rework.

## 2. Inspection

- [ ] **2.1** Parts, orientation, polarity, and pin 1 match the assembly drawing, and DNP parts are absent.
- [ ] **2.2** Solder joints are inspected under magnification, with X-ray for BGAs and other bottom-terminated parts where available.
- [ ] **2.3** Resistance to ground is measured on every rail before power and compared across several boards.
  A short or near-short shows up here as a reading, not as smoke.
- [ ] **2.4** Neighboring rails are checked for shorts between them.
- [ ] **2.5** A board is test-fitted in the enclosure or a 3D print: mounting holes, connectors, buttons, and tall parts.

## 3. First power

- [ ] **3.1** The first board is powered from a current-limited supply set just above the expected current.
- [ ] **3.2** Rails are brought up one at a time where the board allows, with downstream loads isolated through links.
- [ ] **3.3** Input current is recorded and compared with the estimate before going further.
- [ ] **3.4** Each rail voltage is measured at the load, not only at the regulator.
  Drops across traces, links, and connectors show up only at the far end.
- [ ] **3.5** No part runs hot, checked with a thermal camera or a careful touch.
- [ ] **3.6** Sequencing and ramp times are captured on a scope and meet every chip requirement.
- [ ] **3.7** Ripple and noise are measured on each rail with a short ground connection at the probe tip.
  A long ground lead picks up switching noise that is not on the rail.
- [ ] **3.8** The board starts reliably over many power cycles, with both fast and slow supply ramps.

## 4. Clocks and reset

- [ ] **4.1** Reset releases only after the rails are stable, with a clean edge and no glitches.
- [ ] **4.2** Every oscillator runs at the right frequency, measured at a clock-output pin or buffered test point.
- [ ] **4.3** Boot and strap pins are at their intended levels when reset releases.
- [ ] **4.4** A supply that sags slowly or drops quickly causes a clean reset and recovery.

## 5. Programming and debug

- [ ] **5.1** The debug probe connects and reads the device ID, and serial log output works.
- [ ] **5.2** Flash programs and verifies, and option bytes and fuses are as intended.
  Check that read protection or debug lock was not set by accident.
- [ ] **5.3** Firmware reads the board revision correctly.
- [ ] **5.4** The board recovers from an interrupted or bad firmware load.

## 6. Peripherals

- [ ] **6.1** Each subsystem is brought up on its own, in the planned order, against a written pass criterion.
- [ ] **6.2** Every bus is checked with a logic analyzer and a scope: addresses, levels, and rise times with the actual pull-ups.
  A logic analyzer shows the protocol; only a scope shows slow edges and ringing.
- [ ] **6.3** Memory passes full read and write patterns across its whole range.
  A single location can pass with swapped or shorted address lines.
- [ ] **6.4** High-speed links are checked for signal quality at the receiver and error counts over long runs.
- [ ] **6.5** Analog inputs are checked for noise, offset, and gain against a known reference.
- [ ] **6.6** Every connector is exercised with the real cable or mating hardware, including hot-plug where the product allows it.
- [ ] **6.7** Buttons, LEDs, displays, sensors, and actuators work, with motors tested under load.

## 7. RF

- [ ] **7.1** Conducted output power, frequency error, and harmonics are measured through the test connector.
- [ ] **7.2** The antenna match is measured and tuned on assembled boards inside the enclosure.
  A match tuned on a bare board shifts once the enclosure, battery, and hand are near it.
- [ ] **7.3** Radiated performance is checked in a chamber, or at least with comparative range tests.
  A good match alone does not prove the antenna radiates well.
- [ ] **7.4** Receiver sensitivity or packet error rate is checked at low signal levels.
- [ ] **7.5** Radio performance holds with the rest of the board active: regulators, displays, and fast clocks.

## 8. Power consumption

- [ ] **8.1** Current is measured in each operating mode, rail by rail, and compared with the power budget.
- [ ] **8.2** Sleep current is measured with the debugger removed and the device power-cycled.
  On some processors, debug logic keeps running until the next power cycle.
- [ ] **8.3** Burst currents are captured with an instrument fast enough to see them, and the supply stays above brown-out.
- [ ] **8.4** Any gap between measurement and budget is traced: pull-ups, floating inputs, back-powered chips, LEDs.
- [ ] **8.5** Long captures include rare events such as reconnects, retries, and update checks.
  Rare events can dominate the average current.

## 9. Early compliance checks

- [ ] **9.1** A near-field probe scan finds the noisiest areas and cables.
  Emissions problems found now can still be fixed in the next layout.
- [ ] **9.2** Exposed connectors and buttons are tried with an ESD simulator.
- [ ] **9.3** Temperatures are checked in the closed enclosure at the highest expected ambient.

## 10. Issues and rework

- [ ] **10.1** Each issue is logged with the board, symptom, root cause, fix, and status.
- [ ] **10.2** Every rework is recorded against the board serial number, with what changed, why, and a photo.
- [ ] **10.3** A fix is proven on more than one board before it counts as fixed.
  A fix that works on one board may only be hiding a marginal part.
- [ ] **10.4** Key measurements are repeated on several boards to see the spread.

## 11. For the next spin

- [ ] **11.1** Every schematic, layout, and value change is listed and tied to the issue behind it, including values changed on the bench.
- [ ] **11.2** Measured results are fed back into the power budget and the requirements.
- [ ] **11.3** Bring-up aids to keep or remove (jumpers, links, test headers) are decided deliberately.
  Until the design is stable, they are cheap insurance on the next spin too.
- [ ] **11.4** A short review records what was tested, what failed, the root cause, and who owns each fix.

## Related reading

- [Before your first board spin](https://westlakesys.com/articles/first-board-spin/)
- [Battery-powered design: budgeting and measuring power](https://westlakesys.com/articles/battery-power/)
- [Battery life estimator](https://westlakesys.com/tools/battery-life/)
- [Crystal load capacitor calculator](https://westlakesys.com/tools/crystal-load-caps/)
- Next step: [EMC pre-scan checklist](emc-pre-scan.md)

---

From [Westlake Systems](https://westlakesys.com/). Licensed under [CC BY 4.0](../LICENSE): reuse and adapt freely, with credit and a link to the original page.
