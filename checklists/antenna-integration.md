# Antenna and RF integration checklist

How to get a radio and antenna working in a real product: requirements, antenna choice, placement, matching, testing, coexistence, and production.

Interactive and printable version: [https://westlakesys.com/tools/checklists/antenna-integration/](https://westlakesys.com/tools/checklists/antenna-integration/)

A working list for putting a radio and antenna into a product, for teams doing their own RF work. Range problems often come from the antenna's surroundings rather than the radio, so the checks follow the antenna from the first layout to the production line.

Measure in the enclosure, with the battery, cables, and display in place, and with a hand or body nearby if the product will be used that way.

## 1. Requirements

- [ ] **1.1** The range, data rate, and link conditions are written down: indoors or outdoors, through walls or not, and the worst orientation.
- [ ] **1.2** A link budget uses real figures for transmit power, receiver sensitivity, antenna gain in the enclosure, cable and connector losses, and a fade margin.
  The radio range estimator in Tools does the arithmetic.
- [ ] **1.3** Bands, channels, and power limits are set for every market the product will ship to.
- [ ] **1.4** The approval route is chosen: a certified module used exactly as its grant allows, or a chip-down radio with full radio testing.
- [ ] **1.5** Transmit power is checked as radiated power in the antenna's strongest direction, conducted power plus peak gain minus losses, against each market's limit.
  An antenna with a strong peak in one direction lowers the conducted power you can use.

## 2. Antenna choice

- [ ] **2.1** The antenna type suits the enclosure and the space available: chip, PCB trace, flexible, or external.
- [ ] **2.2** Gain and efficiency figures come from a ground plane like yours, or will be measured on your board.
  Datasheet figures assume the vendor's reference board; on a smaller board, efficiency can be much lower.
- [ ] **2.3** With a module, the antenna is one its approval lists, or the cost of adding a different one is understood.
- [ ] **2.4** An external or detachable antenna meets each market's connector rules and matches the antennas named in the approval.
  In the US, an antenna the user can remove needs a non-standard connector.

## 3. Placement and enclosure

- [ ] **3.1** The antenna sits where its vendor recommends, usually at an edge or corner, with the keep-out clear on every layer.
- [ ] **3.2** Metal, batteries, displays, and wiring stay at least the distance the vendor gives from the antenna.
- [ ] **3.3** The enclosure near the antenna is plastic or another RF-transparent material, with coatings, paints, and metal inserts checked.
  Some paints and platings contain metal and detune the antenna.
- [ ] **3.4** How the product is held, worn, or mounted is accounted for, since a hand, a wrist, or a metal surface nearby shifts the tuning.
- [ ] **3.5** Noisy circuits, such as switching regulators, clocks, displays, and camera interfaces, are kept away from the antenna and the RF path.
- [ ] **3.6** The keep-out is drawn as a rule area in the layout on every affected layer, so a later copper pour or reroute cannot fill it.

## 4. Feed line and matching

- [ ] **4.1** The feed line from the radio to the antenna is a short 50-ohm line over solid ground, with stitching vias along both sides.
- [ ] **4.2** An external antenna or exposed antenna connector has ESD protection suited to the RF path, such as a low-capacitance suppressor or a shunt inductor.
- [ ] **4.3** A pi matching network footprint sits between the radio and the antenna, fitted with a zero-ohm link and empty shunt positions to start.
  With three positions, either L-network orientation can be fitted, so almost any load can be matched.
- [ ] **4.4** The match is tuned with a vector network analyzer on the board in its final enclosure, with all parts in place.
- [ ] **4.5** The analyzer's reference plane is moved to the matching network, by calibrating at the end of the pigtail or with port extension, and the test cable is kept from becoming part of the antenna.
  On a small board, ferrites on the cable or a sleeve balun reduce the error.
- [ ] **4.6** The tuning covers the whole band and holds across production part tolerances.
- [ ] **4.7** An active antenna powered through its RF cable has a current limit, so a shorted cable cannot pull down the supply or burn out the bias inductor.

## 5. Conducted tests

- [ ] **5.1** Transmit power, frequency error, and harmonics are measured at the test connector on low, middle, and high channels.
- [ ] **5.2** Receiver sensitivity is measured at the test connector, first with the radio alone, then with the whole product running.
- [ ] **5.3** Any drop in sensitivity with the product running is traced to its source.
  Desense from clocks, regulators, or displays cuts range as surely as a poor antenna.

## 6. Radiated tests

- [ ] **6.1** Total radiated power and sensitivity are measured in a chamber, or compared over the air against a known-good reference device.
  Cellular carriers set minimum radiated figures for their own certification.
- [ ] **6.2** A range test is run in the real setting, in the worst orientation, and compared with the link budget.
- [ ] **6.3** Over-the-air sensitivity is checked with the display, charger, and every interface active.

## 7. Coexistence

- [ ] **7.1** Radios that share a band, such as Bluetooth and Wi-Fi, have coexistence signals or time sharing set up in hardware and firmware.
- [ ] **7.2** Each transmitter's harmonics and spurious outputs are checked against the other radios' receive bands.
- [ ] **7.3** A GNSS receiver is checked for desense from the other radios and from digital noise near its band.
  GNSS signals arrive below the thermal noise floor, so even small amounts of board noise cost sensitivity.
- [ ] **7.4** Isolation between antennas for different radios is measured, and the antennas are separated or oriented to improve it.
- [ ] **7.5** Op-amp and sensor amplifier inputs near the antenna or on cables have an RF filter, and their rejection of RF at the transmit frequency is looked up where the datasheet gives it, or tested.
  Amplifier input stages rectify RF into a DC offset that looks like a measurement error and follows the radio's activity.

## 8. Production

- [ ] **8.1** Production test checks every unit's RF path, at least transmit power and a receive check, with limits set from measured units.
- [ ] **8.2** The test fixture, cables, and limits are checked against a known-good unit at the start of each run.
- [ ] **8.3** Per-unit calibration, such as crystal frequency trim or transmit power, is written where the radio needs it.
- [ ] **8.4** The antenna, matching parts, and enclosure materials are locked in the BOM, and any substitute is retested.

## Related reading

- [Choosing a radio: matching the wireless technology to the product](https://westlakesys.com/articles/choosing-a-radio/)
- [Module or chip-down: making the radio decision](https://westlakesys.com/articles/module-or-chip-down/)
- [Radio range estimator](https://westlakesys.com/tools/radio-range/)
- [UWB design review checklist](https://westlakesys.com/tools/checklists/uwb-design-review/)
- Next step: [EMC pre-scan checklist](emc-pre-scan.md)

---

From [Westlake Systems](https://westlakesys.com/). Licensed under [CC BY 4.0](../LICENSE): reuse and adapt freely, with credit and a link to the original page.
