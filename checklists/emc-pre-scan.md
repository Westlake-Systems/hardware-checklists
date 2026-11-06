# EMC pre-scan checklist

How to run an in-house EMC pre-scan before formal testing: setup, near-field scans, radiated and conducted emissions, ESD, and fixes.

Interactive and printable version: [https://westlakesys.com/tools/checklists/emc-pre-scan/](https://westlakesys.com/tools/checklists/emc-pre-scan/)

A working list for checking emissions and immunity in-house before a product goes to a test lab, for teams doing their own pre-compliance work. A pre-scan cannot pass a product, but it finds problems early, while they are still cheap to fix.

Bench readings are relative, not absolute. Compare them with the limit using a margin set up front, compare each fix with the reading before it, and confirm the results in a pre-compliance session at a lab.

## 1. Setup

- [ ] **1.1** The product is set up as it will be tested: final enclosure if available, real cables at their real lengths, and firmware in its noisiest mode.
  Emissions change with cable routing and firmware activity, so record both.
- [ ] **1.2** Firmware has test modes for continuous transmit, maximum processor and bus activity, each display or motor state, and charging from a typical adapter.
- [ ] **1.3** The spectrum analyzer or EMI receiver covers the frequencies the standard needs, with its detectors and resolution bandwidths set as the standard specifies.
- [ ] **1.4** The ambient is measured and saved with the product off, so local radio, TV, and cellular signals are not mistaken for the product.
- [ ] **1.5** The analyzer is checked for overload: an external 10 dB attenuator at the input should lower every peak by exactly 10 dB.
  A peak that drops by more, or disappears, was created inside the analyzer by strong local signals.
- [ ] **1.6** Each setup is photographed and recorded, with cable positions, probe or antenna positions, distances, and settings, so later scans can be repeated.

## 2. Near-field scan

- [ ] **2.1** A near-field probe set is on hand, with H-field loops and an E-field probe, plus a preamplifier if the analyzer needs one.
- [ ] **2.2** Clocks, switching regulators, processors, memory, and every cable connector are scanned, and the hot spots are marked on a board photo.
- [ ] **2.3** Each peak is matched to a source by its frequency: a clock and its harmonics, a regulator switching frequency, or a data rate.
  Turning subsystems on and off one at a time confirms which one a peak belongs to.
- [ ] **2.4** Cable connectors and enclosure seams get the closest look.
  Below a few hundred megahertz, emissions from a small product usually leave on its cables rather than from the board.
- [ ] **2.5** Near-field readings are used to compare before and after a fix, not to predict a pass.

## 3. Radiated emissions

- [ ] **3.1** A current probe on each cable measures common-mode current, the main source of radiation from cables.
  A few microamps of common-mode current at tens of megahertz and above, on a meter of cable, can be enough to exceed a residential limit.
- [ ] **3.2** Where an antenna measurement is possible, the distance, antenna height, and product orientation are recorded, and the product is turned to find the worst case.
- [ ] **3.3** Each peak is compared with the limit for the target class, residential or commercial, after correcting for antenna factor, cable loss, and measurement distance, using the agreed margin.
- [ ] **3.4** Peaks are found with a fast peak scan, and only those near the limit are remeasured with the quasi-peak or average detector the standard uses.
- [ ] **3.5** If the product generates or uses any frequency above 108 MHz, emissions are measured above 1 GHz.
  The upper end of the scan is set by the highest frequency the product generates or uses, and above 1 GHz the detectors and bandwidths change.

## 4. Conducted emissions

- [ ] **4.1** Mains-powered products, including those with an external supply, are measured through a LISN on the AC input from 150 kHz to 30 MHz.
- [ ] **4.2** The LISN, product, and cables sit on a ground plane in a repeatable layout, as the standard describes, with the LISN bonded to the plane.
  The LISN port not being measured is terminated in 50 ohms.
- [ ] **4.3** The analyzer input is protected with a transient limiter or attenuator, with its loss entered as an offset.
  Switching power through a LISN can send a transient that damages the input.
- [ ] **4.4** Wired network ports, such as Ethernet, are checked for conducted emissions through an impedance stabilization network where the target markets require it.

## 5. ESD and immunity

- [ ] **5.1** An ESD simulator is applied at the levels of the target standard: contact discharge to metal a user can touch, air discharge to insulating surfaces such as seams, plastic buttons, and the display, and indirect discharge to the coupling planes.
- [ ] **5.2** Pass criteria are written before testing: what the product may do during a discharge, and how it must recover.
  The standards group these as performance criteria A, B, and C.
- [ ] **5.3** Where the target markets require immunity testing, power and long signal cables are tried with fast transients and surges.
- [ ] **5.4** Radiated immunity gets a rough check with a handheld radio you are allowed to operate, held at a set distance.
  It covers only a few frequencies, so it is a sanity check, not a sweep.
- [ ] **5.5** Firmware recovers by itself from a reset, a lockup, or a corrupted bus, with a watchdog running.

## 6. Fixes

- [ ] **6.1** Fixes are tried one at a time, rescanned, and recorded with readings from before and after.
- [ ] **6.2** Fixes start at the source with the cheapest change: firmware edge rates and clock settings first, then parts on reserved footprints, then ferrites and shields.
  Spread-spectrum clocking lowers peaks where the interfaces tolerate it.
- [ ] **6.3** Each fix is checked for side effects on signal integrity, radio sensitivity, and power consumption.
- [ ] **6.4** Every fix that works on the bench is carried into the schematic, layout, and BOM for the next spin.

## 7. Before the lab

- [ ] **7.1** The worst emissions have margin against the limit in the final configuration.
- [ ] **7.2** The product, cables, and firmware going to the lab match what was pre-scanned.
- [ ] **7.3** A pre-compliance session at a lab is booked on hardware close to final, with a list of the frequencies to look at first.
- [ ] **7.4** Results are filed with the board revision and firmware version they were measured on.

## Related reading

- [Plan for compliance from day one](https://westlakesys.com/articles/compliance-from-day-one/)
- [Before your first board spin](https://westlakesys.com/articles/first-board-spin/)
- [Schematic and layout review checklist](https://westlakesys.com/tools/checklists/design-review/)
- Next step: [Compliance readiness checklist](compliance-readiness.md)

---

From [Westlake Systems](https://westlakesys.com/). Licensed under [CC BY 4.0](../LICENSE): reuse and adapt freely, with credit and a link to the original page.
