# EVT, DVT, and PVT exit checklist

What each hardware build should prove before the next: planning, EVT, DVT, and PVT exit criteria, design freeze, and the review after every build.

Interactive and printable version: [https://westlakesys.com/tools/checklists/evt-dvt-pvt/](https://westlakesys.com/tools/checklists/evt-dvt-pvt/)

What to confirm before leaving each build on the way from prototype to production, for teams running their own builds. Each stage answers one question: does the design work, does it hold up, and can the factory build it repeatedly.

Small teams often merge stages or use a pilot run in place of PVT. That works if the merged build still answers every question; check the items for each stage either way.

## 1. Before EVT

- [ ] **1.1** Requirements are written down: what the product must do, where it will be sold, and how it will be used.
- [ ] **1.2** The riskiest parts of the architecture have been tried on prototypes or development kits.
- [ ] **1.3** The main parts are chosen, with availability, lead time, lifecycle status, and second sources checked.
- [ ] **1.4** If a contract manufacturer is chosen, it has reviewed the design for part choices, panelization, and test access.
  Their feedback is cheapest to act on before layout is settled.
- [ ] **1.5** The boards have debug access, test points, and current-measurement points for bring-up, with room kept for production test points and a firmware test mode.

## 2. Planning each build

- [ ] **2.1** The question the build must answer, and its exit criteria, are written down before the build is ordered.
- [ ] **2.2** Unit counts cover every use: testing, firmware, certification, reliability units that will be destroyed, and demos.
  Too few units means a second, small, expensive run.
- [ ] **2.3** Long-lead parts, fixtures, and any tooling the build needs are ordered early enough for the build date.
- [ ] **2.4** Each unit has a serial number, and its hardware revision, firmware version, and any rework are recorded.
- [ ] **2.5** The test plan lists who tests what, on which units, and where the results are kept.

## 3. EVT exit

- [ ] **3.1** Every function and interface has been demonstrated on the custom boards.
  The first board bring-up checklist covers the first power-on and the checks after it.
- [ ] **3.2** Power is measured against the requirements in every operating mode, including sleep and off.
- [ ] **3.3** Firmware runs on the real hardware, with test modes for certification and production test.
- [ ] **3.4** Early compliance checks are done: near-field scans and ESD on the bench, with fixes carried into the design.
- [ ] **3.5** Major bugs are fixed, or understood with a planned fix.
- [ ] **3.6** The mechanical design is stable enough to order production tooling, after a manufacturability review with the toolmaker.
  Tooling takes weeks to build and several rounds of trial shots to adjust.

## 4. DVT build

- [ ] **4.1** Boards come from the intended assembler, built with the production process.
- [ ] **4.2** Enclosure parts come from production tooling after its first trial shots and adjustments.
- [ ] **4.3** The design changes since EVT are all listed, and each one has been checked.
- [ ] **4.4** A first version of the production test fixture is ready, so DVT units prove the fixture as well as the product.

## 5. DVT exit

- [ ] **5.1** Reliability and environmental tests pass, or the fixes are known and verified, with tests chosen to match how the product is used: temperature, humidity, drop, vibration, and wear.
  For outdoor products, include time in real sun.
- [ ] **5.2** The product starts up at each temperature extreme, not only runs through the range.
  Powering on warm and then cooling proves the product runs cold, not that it starts cold.
- [ ] **5.3** Battery life, thermal behavior, and radio performance are measured in the final enclosure.
- [ ] **5.4** Pre-compliance passes at a lab, and formal certification testing is under way or done on units that represent production.
- [ ] **5.5** Parts from the tools are inspected against the drawings, and cosmetics and fit are approved.
- [ ] **5.6** Assembly defects from the build are reviewed with the assembler, and design-side causes are fixed.
- [ ] **5.7** The design is frozen, and any change after this point goes through a written change process.
  Each change is checked against tooling, certification, and the factory instructions; late mechanical changes are kept steel-safe, so the toolmaker removes metal rather than adding it.

## 6. PVT build

- [ ] **6.1** Units are built on the production line by trained operators, using production tooling, fixtures, assembly instructions, and packaging.
- [ ] **6.2** Units are programmed with released production firmware through the line's own process, including any unique IDs and keys.
- [ ] **6.3** Work instructions for each station, and inspection criteria for incoming parts, the line, and finished units, are agreed with the contract manufacturer.
- [ ] **6.4** Labels, regulatory marks, and the manual are final, and certification is complete before any unit is sold.
  PVT units are often the first ones sold.

## 7. PVT exit

- [ ] **7.1** The line runs at the intended rate, and yield meets the target agreed with the contract manufacturer.
- [ ] **7.2** Every failure is understood, with root causes and fixes recorded.
- [ ] **7.3** The production test catches real defects without rejecting good units, and its results are logged.
- [ ] **7.4** First article inspection confirms assemblies match the drawings, and packaged units pass drop and transit testing.
- [ ] **7.5** The design is unchanged since DVT, or each change has gone through the change process.
- [ ] **7.6** A golden unit and cosmetic limit samples are kept as the reference for what production should look like.

## 8. After every build

- [ ] **8.1** A short review records what was tested, what failed, the root cause, and who owns each fix.
- [ ] **8.2** Every fix is carried into the schematic, layout, BOM, firmware, and drawings before the next build.
- [ ] **8.3** The schedule and unit counts for the next build are updated from what this one showed, including another build of the same stage if its exit criteria are not met.

## Related reading

- [Checklist for choosing a contract manufacturer](https://westlakesys.com/tools/checklists/choosing-a-contract-manufacturer/)
- [From prototype to production: EVT, DVT, and PVT explained](https://westlakesys.com/articles/prototype-to-production/)
- [Designing for production test](https://westlakesys.com/articles/designing-for-production-test/)
- [What a complete manufacturing package includes](https://westlakesys.com/articles/manufacturing-package/)
- Next step: [Release to manufacturing checklist](manufacturing-release.md)

---

From [Westlake Systems](https://westlakesys.com/). Licensed under [CC BY 4.0](../LICENSE): reuse and adapt freely, with credit and a link to the original page.
