# Release to manufacturing checklist

What to include and confirm before releasing a design to a board fab and contract manufacturer: data, BOM, programming, test, labels, and revisions.

Interactive and printable version: [https://westlakesys.com/tools/checklists/manufacturing-release/](https://westlakesys.com/tools/checklists/manufacturing-release/)

What to confirm before a design goes to a board fab and contract manufacturer, for teams preparing their own release. A complete package lets the factory quote, build, program, and test your product without guessing.

Use it before the first prototype order as well as the production release; most of the gaps that stop a build show up on both.

## 1. Board fabrication

- [ ] **1.1** Layer data is in Gerber X2, ODB++, or IPC-2581.
  Older Gerbers carry no layer function, so the fab has to work out which file is which.
- [ ] **1.2** Drill files keep plated and non-plated holes clearly separate.
- [ ] **1.3** Stackup and impedance requirements state layer count, copper weights, dielectrics, target impedances, tolerances, and reference layers.
- [ ] **1.4** The fab notes say whether the fab may adjust trace widths to hit impedance targets.
- [ ] **1.5** The fabrication drawing states material, finish, mask and silkscreen colors, IPC-6012 or IPC-6013 class, outline tolerances, and special features.
- [ ] **1.6** An IPC-D-356 test netlist is included if you send Gerbers.
- [ ] **1.7** Panel requirements say who designs the panel, with fiducials, tooling holes, and tabs or V-score.

## 2. Bill of materials

- [ ] **2.1** Every line has reference designators, quantity, manufacturer, and manufacturer part number.
  A distributor stock number alone is not enough; the assembler may buy elsewhere.
- [ ] **2.2** Critical and long-lead parts have approved alternates listed.
  Without them, every shortage becomes a phone call and a delay.
- [ ] **2.3** Every part is active, in stock in the build quantity, and not marked not recommended for new designs.
- [ ] **2.4** Passive lines specify tolerance, voltage rating, dielectric, and package, not just a value.
  A value and size alone leave the assembler to choose the rest.
- [ ] **2.5** Parts with no schematic symbol are in the BOM: labels, gaskets, light pipes, screws, and standoffs.
  Nobody draws them on the schematic, so they are easy to leave out.
- [ ] **2.6** Moisture-sensitive parts are identified so the assembler handles them correctly.

## 3. Assembly data

- [ ] **3.1** Pick-and-place data covers position, rotation, and side for every part, in the same units and origin as the board data.
- [ ] **3.2** The BOM and pick-and-place data agree: no missing parts, no extras, and rotations that match the footprints.
- [ ] **3.3** DNP parts agree across the BOM, pick-and-place, and assembly drawing.
  A part that is DNP in the BOM but present in the placement file can easily get placed.
- [ ] **3.4** Stencil requirements are stated where defaults will not do: thickness, step areas, and thermal pad apertures.
- [ ] **3.5** The assembly drawing shows polarity, pin 1, hand-soldered parts, adhesive, coating keep-outs, and heat sinks.
- [ ] **3.6** Parts whose pin 1 or polarity marking varies between vendors have explicit orientation notes.
- [ ] **3.7** Lead-free or leaded assembly and the IPC-A-610 acceptance class are stated.

## 4. Design reference

- [ ] **4.1** The schematic is included as a PDF at the release revision.
- [ ] **4.2** A 3D model of the assembled board is included for the mechanical and box-build side.
- [ ] **4.3** Known deviations are listed: rework, patch wires, and parts that differ from the schematic.

## 5. Mechanical and box build

- [ ] **5.1** Enclosure drawings and models are at the release revision.
- [ ] **5.2** Cable and harness drawings show connectors, pinouts, lengths, and labeling.
- [ ] **5.3** Every piece of hardware has a part number, with torque values where they matter.
- [ ] **5.4** Box-build instructions go step by step, with photos or exploded views.

## 6. Firmware and programming

- [ ] **6.1** Released firmware images are named with their version and a checksum.
- [ ] **6.2** A written programming procedure covers the tool, connector, order of processors, option bytes, read protection, and how to confirm the load.
- [ ] **6.3** The source and record of per-unit data are defined: serial number, MAC address, calibration data, and keys.
  You should be able to look up what each serial number received.
- [ ] **6.4** Keys and credentials have their own secure provisioning process, and the signing key never sits on a line PC.
- [ ] **6.5** Debug access is locked or disabled on production units.
  An open debug port lets anyone read and replace the firmware.
- [ ] **6.6** The firmware version can be read from a finished unit.

## 7. Test

- [ ] **7.1** A test specification defines what to test, the pass and fail limits, and the records to keep for each unit.
- [ ] **7.2** The test fixture is described: test points, power, the interfaces it drives, and its software.
- [ ] **7.3** Production RF test and any per-unit calibration are defined for products with a radio.
- [ ] **7.4** Test time per unit is estimated and fits the line rate.
  A slow test station becomes the bottleneck for the whole line.
- [ ] **7.5** Failed units have a defined path: retest, repair, scrap, and how results are logged.

## 8. Labels and packaging

- [ ] **8.1** Label artwork and placement are defined, with the serial number and date code format.
- [ ] **8.2** Regulatory markings and IDs match what was certified, for every market.
- [ ] **8.3** Packaging is defined: box, inserts, what ships in the box, and how units are packed for shipping.

## 9. Revision control

- [ ] **9.1** Every file carries the same release revision, in its title block, file name, or both.
  When revisions disagree, the manufacturer cannot tell which file is right.
- [ ] **9.2** The package is one archive named with the product and revision, with a readme listing contents, date, and contact.
- [ ] **9.3** Outputs are generated by script from a tagged source revision.
  Hand-built packages drift: an output setting changes or a file comes from the wrong revision.
- [ ] **9.4** Design and electrical rule checks pass on the released revision.
- [ ] **9.5** The released set is read-only, and any change is a new revision with a note on what changed.
- [ ] **9.6** The engineering change order process is agreed with the manufacturer: what changed, why, which units, and what happens to stock.

## 10. Before the build

- [ ] **10.1** The manufacturer has reviewed the package and their questions are answered.
  Their questions show what is missing while it is still cheap to fix.
- [ ] **10.2** The board fab and assembler have run their own manufacturability checks.
- [ ] **10.3** The certified configuration (hardware revision, firmware version, antenna) matches the release.
  A release that differs from what was certified can need retesting.
- [ ] **10.4** A first article inspection plan confirms parts and assemblies match the drawings.
- [ ] **10.5** The pilot build has a set quantity, goals, and the full test process.
- [ ] **10.6** The yield target is agreed with the contract manufacturer.
- [ ] **10.7** A golden unit or sample set is kept as the reference for production.

## Related reading

- [EVT, DVT, and PVT exit checklist](https://westlakesys.com/tools/checklists/evt-dvt-pvt/)
- [What a complete manufacturing package includes](https://westlakesys.com/articles/manufacturing-package/)
- [From prototype to production: EVT, DVT, and PVT explained](https://westlakesys.com/articles/prototype-to-production/)
- [What I look for in a hardware design review](https://westlakesys.com/articles/design-review/)

---

From [Westlake Systems](https://westlakesys.com/). Licensed under [CC BY 4.0](../LICENSE): reuse and adapt freely, with credit and a link to the original page.
