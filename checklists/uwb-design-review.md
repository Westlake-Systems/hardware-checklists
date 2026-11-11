# UWB design review checklist

Checks for an ultra-wideband ranging or positioning design: requirements, regulation, link budget, antenna, layout, calibration, firmware, and test.

Interactive and printable version: [https://westlakesys.com/tools/checklists/uwb-design-review/](https://westlakesys.com/tools/checklists/uwb-design-review/)

A working list for reviewing an ultra-wideband (UWB) ranging or positioning design before the board order, and again before the enclosure is tooled. UWB transmit power is capped by regulation, so range and accuracy are decided by the antenna, the receive path, calibration, and the settings, and those are where the checks concentrate.

It adds to the schematic and layout review and the antenna and RF integration checklists; it does not replace them.

## 1. Requirements

- [ ] **1.1** Accuracy is written as a number with its conditions: the error, how often it may be exceeded, at what distance, and in what orientation.
  The tail of the error distribution is what users notice.
- [ ] **1.2** The range needed is stated for the worst orientation and placement, with a body or wall in the path if that can happen in use.
- [ ] **1.3** The update rate and the number of devices in range at once are set.
  Together they set time on the air, which sets battery life and how many devices can share a channel.
- [ ] **1.4** The topology is chosen: two-way ranging between devices, or fixed anchors using time difference of arrival.
  Two-way ranging needs no shared clock. Time difference of arrival lets tags transmit and sleep, but the anchors must be synchronized.
- [ ] **1.5** What the product does with a missing or doubtful measurement is decided.

## 2. Regulation and channels

- [ ] **2.1** A channel is chosen for every market the product will ship to.
  The channels near 6.5 GHz and 8 GHz are the most widely accepted. Other bands carry extra conditions in some regions.
- [ ] **2.2** The rule category matches the use: indoors, handheld, outdoors, or in a vehicle.
  The rules differ by market, and fixed outdoor installations are where they differ most. Check them early if anything will be mounted outside.
- [ ] **2.3** The link budget respects both the average power density limit and the peak limit, as radiated power.
- [ ] **2.4** If the channel overlaps 6 GHz Wi-Fi, interference in both directions has been considered.
- [ ] **2.5** The approval route is chosen: a certified module used exactly as its approval allows, or a chip-down radio with full radio testing.

## 3. Link budget

- [ ] **3.1** A link budget exists, with radiated power at the limit, antenna efficiency in the enclosure at both ends, front-end losses, and receiver sensitivity for the chosen settings.
- [ ] **3.2** The budget includes margin for a body or hand in the path, if the product is carried or worn.
- [ ] **3.3** Data rate and preamble length are chosen for the product, not left at the reference firmware defaults.
  Lower rates and longer preambles add range and cost time on the air.
- [ ] **3.4** Every loss between the chip and the antenna is counted: balun, filter, switch, trace, and connector.
- [ ] **3.5** Any amplifier in the receive or transmit path is justified against its current, and its switching and settling times fit the frame timing.

## 4. Antenna and enclosure

- [ ] **4.1** The antenna's bandwidth covers the channels in use, with margin, when measured in the enclosure.
  A UWB channel is 500 MHz or more wide, so detuning that a narrowband antenna tolerates can cut into it.
- [ ] **4.2** Efficiency and pattern are measured in the enclosure, with the battery, cables, and display in place.
- [ ] **4.3** The peak antenna gain is known.
  The power limit applies in the strongest direction, so a peaky pattern lowers the power allowed in every other direction.
- [ ] **4.4** For tight accuracy targets, the change in antenna delay with direction has been measured.
  It shows up as a distance error that changes as the device turns.
- [ ] **4.5** Polarization at both ends suits how the devices are held or mounted.
- [ ] **4.6** For angle of arrival, element spacing, matched feed lengths, and phase calibration are defined.
- [ ] **4.7** Coatings, potting, paint, and labels over the antenna have been checked for detuning.

## 5. Schematic and layout

- [ ] **5.1** The RF path follows the chip vendor's reference design, and the board stackup matches the dimensions that design assumes.
- [ ] **5.2** RF and PLL supplies are decoupled as the datasheet requires, and switching regulators are kept away from them.
- [ ] **5.3** The crystal meets the frequency tolerance the radio needs, its load capacitors are sized, and the trim range covers the spread.
  The crystal load capacitor calculator in Tools does the arithmetic.
- [ ] **5.4** The supply holds up under transmit and receive current peaks, at the lowest battery voltage and temperature.
- [ ] **5.5** Reset, wake, interrupt, and bus signals are connected and timed as the datasheet requires.

## 6. Timing and calibration

- [ ] **6.1** Antenna delay is calibrated, and the method and the place the value is stored are defined.
- [ ] **6.2** Transmit power is calibrated for each channel against the limit, with a stated margin.
  Per-unit calibration lets every unit sit close to the limit.
- [ ] **6.3** Each unit's crystal is trimmed in production, or the design tolerates the untrimmed spread.
- [ ] **6.4** The effect of temperature on the crystal, the delays, and transmit power is compensated or budgeted.
- [ ] **6.5** Calibration values survive a firmware update and a factory reset.

## 7. Firmware and system

- [ ] **7.1** The ranging scheme cancels the clock offset between devices.
- [ ] **7.2** Scheduling handles many devices in range without collisions, and anchors stay synchronized where they need to be.
- [ ] **7.3** Measurements taken without a clear direct path are detected and flagged or rejected.
  A blocked direct path reads long; this is the largest real-world error.
- [ ] **7.4** Filtering suits how fast the devices move, and the delay it adds is acceptable.
- [ ] **7.5** The UWB receiver is on only when needed, with discovery handled by a schedule or a second radio.
- [ ] **7.6** Where a distance unlocks or authorizes something, secure ranging is used and relay attacks have been considered.

## 8. Test

- [ ] **8.1** Range and accuracy are tested in a place like the one the product will live in, in the enclosure, with people present.
- [ ] **8.2** Results are recorded as a distribution across orientations, not as a best case or an average.
- [ ] **8.3** The production test checks transmit power, frequency, and a ranging measurement against a reference, within a set time.
- [ ] **8.4** A reference unit is kept for the production test and is itself checked on a schedule.

## Related reading

- [Why UWB range falls short of the datasheet](https://westlakesys.com/articles/uwb-range/)
- [Measuring distance with radio](https://westlakesys.com/articles/radio-ranging/)
- [Antenna and RF integration checklist](https://westlakesys.com/tools/checklists/antenna-integration/)
- Next step: [EMC pre-scan checklist](emc-pre-scan.md)

---

From [Westlake Systems](https://westlakesys.com/). Licensed under [CC BY 4.0](../LICENSE): reuse and adapt freely, with credit and a link to the original page.
