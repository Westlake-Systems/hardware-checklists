# Compliance readiness checklist

What to settle before you book a compliance test lab: markets and standards, radio approach, design checks, pre-scans, test modes, samples, and paperwork.

Interactive and printable version: [https://westlakesys.com/tools/checklists/compliance-readiness/](https://westlakesys.com/tools/checklists/compliance-readiness/)

How to get a product ready for formal compliance testing, for teams preparing their own lab visit. Lab time is expensive and booked well ahead, so arriving ready saves both money and schedule.

Start the first sections early in the design. The later ones fill in as the product nears its final form. This is not legal advice; confirm the current rules for your product and markets.

## 1. Markets and scope

- [ ] **1.1** The list of markets is settled and written down.
  It decides the radio approach, the safety design, and the test plan.
- [ ] **1.2** For each market, the applicable rules are listed: EMC, radio, product safety, energy efficiency, restricted substances, and cybersecurity.
- [ ] **1.3** The product safety standard is chosen for the product type.
- [ ] **1.4** Program certifications are identified where they apply, such as Bluetooth listing, carrier and PTCRB approval, or Matter.
- [ ] **1.5** Responsible parties are named: a US party for FCC declarations, a US agent for FCC certification, a Canadian representative for ISED, an EU importer or authorized representative, and a UK importer.
  A US applicant can act as its own FCC agent; ISED needs a Canadian representative only for applicants outside Canada.
- [ ] **1.6** The chosen lab and certification body are confirmed as recognized for each market.
  Recognition can be withdrawn, so check it close to booking.

## 2. Radio approach

- [ ] **2.1** A module is integrated within its grant: antenna type and gain, trace design, keep-outs, body distance, and co-transmission limits.
  Read the grant and integration instructions before layout, not after.
- [ ] **2.2** For the EU, the plan covers your own assessment of the finished radio product.
  The EU has no modular approval; the module reports support your assessment rather than replace it.
- [ ] **2.3** The host product is planned for its own emissions testing as a digital device, even with a certified module.
- [ ] **2.4** A chip-down radio has a test plan listing the radio standards for each market.
- [ ] **2.5** RF exposure is assessed for how close the antenna sits to the user, and for radios that transmit at the same time.
  An antenna within 20 cm of the body can take a design outside a module grant that assumed more.
- [ ] **2.6** Regional frequency plans, power limits, and airtime rules are reflected in the firmware and hardware variants.

## 3. Design checks

- [ ] **3.1** Fast edges are slowed where possible, and fast signals have solid return paths.
- [ ] **3.2** Cables leaving the enclosure are filtered at the connector.
- [ ] **3.3** Every exposed connector, button, and seam has ESD protection and a planned path for the energy.
- [ ] **3.4** Power and long signal lines can handle fast transients and surges, where the target markets require immunity testing.
  The EU and UK require immunity; the US and Canada mostly do not for commercial products.
- [ ] **3.5** Creepage, clearance, and insulation meet the safety standard wherever hazardous voltages are present.
- [ ] **3.6** A certified external power supply is used where practical, and it meets the US and EU efficiency rules where they apply.
  It keeps mains voltage out of your product entirely.
- [ ] **3.7** Products with a large battery or other high-power source have suitable enclosure materials and protective circuits.
- [ ] **3.8** Rechargeable products in the EU common charger categories, such as phones, headphones, and keyboards, charge through USB-C.
- [ ] **3.9** Products with batteries are checked against each market's battery rules, such as EU labeling, producer registration, and batteries the end user can remove and replace.
  The EU removal and replacement rules apply from 18 February 2027 and shape the enclosure design. The exemptions are narrow.
- [ ] **3.10** The enclosure has room for the required labels and marks.
- [ ] **3.11** Connected products meet each market's security rules, such as no universal default passwords, a way to report vulnerabilities, a stated support period, and secure updates.
  The rules state outcomes; secure boot, locked debug, and protected keys are the usual ways to meet them.

## 4. Pre-scans and freeze

- [ ] **4.1** Early prototypes have been scanned with a near-field probe and the hot spots fixed.
- [ ] **4.2** ESD has been tried on the bench with a simulator.
- [ ] **4.3** A pre-compliance session at a lab has been run on hardware close to final, with margins recorded and fixes verified.
- [ ] **4.4** The design is frozen before formal testing, including the RF circuit, antenna, and radio firmware settings.
  Changes after testing can mean retesting.

## 5. Test modes

- [ ] **5.1** Firmware provides continuous transmit on a chosen channel, modulated and unmodulated.
- [ ] **5.2** Channel, power level, and data rate can be selected, and a receive-only mode is available.
- [ ] **5.3** A worst-case mode runs every interface, display, and motor at once for emissions testing.
  Emissions are measured in the configuration most likely to fail.
- [ ] **5.4** Lab staff can switch modes without a debugger, using documented commands, a button sequence, or a simple tool.
  Setup time at the lab is billed like test time.
- [ ] **5.5** The test firmware version is recorded, and its radio settings match the production firmware.

## 6. Samples and lab files

- [ ] **6.1** Conducted samples with an RF test connector and radiated samples with the production antenna are ready, with spares.
  Labs usually want both, and a spare saves a lost day if a unit fails.
- [ ] **6.2** Support equipment is packed: power supplies, cables, host or accessories, and any software the lab needs.
- [ ] **6.3** Design documents are ready: block diagram, schematics, BOM, layout, antenna specification, and an operational description.
- [ ] **6.4** The test plan is agreed with the lab, and the lab is booked well ahead.

## 7. Declarations and files

- [ ] **7.1** The technical file is assembled: product description, design documents, risk assessment, test reports, and standards applied.
- [ ] **7.2** The EU Declaration of Conformity lists the applicable directives, regulations, and standards, and is signed.
- [ ] **7.3** Records for an FCC Supplier's Declaration of Conformity are kept, with the compliance statement and US responsible party.
- [ ] **7.4** Supplier declarations cover RoHS and REACH, including any substance of very high concern above 0.1% by weight.
  A product containing one also needs a notification to the EU SCIP database.
- [ ] **7.5** WEEE producer registration is in place in each country that requires it.
- [ ] **7.6** Connected products have a documented security risk assessment and a software bill of materials.

## 8. Manual and labeling

- [ ] **8.1** The user manual includes the required regulatory statements for each market, such as FCC Part 15 notices and ISED notices in English and French.
- [ ] **8.2** For EU radio products, the manual lists frequency bands, maximum transmit power, and a simplified Declaration of Conformity.
- [ ] **8.3** Safety warnings and instructions are in the languages of each market.
- [ ] **8.4** Consumer products sold in California are checked for whether they need a Proposition 65 warning, on the product or packaging and where they are sold online.
  Businesses with fewer than 10 employees are exempt, but customers may still require the warning.
- [ ] **8.5** The label carries the right IDs and marks: FCC ID, ISED number, CE or UKCA, the WEEE bin, model, and serial number.
- [ ] **8.6** Manufacturer and importer names and addresses appear on the product, packaging, or accompanying documents as each market requires.
- [ ] **8.7** Electronic labeling is used only where the rules allow it, such as on a product with a built-in display.
- [ ] **8.8** Model names on labels, reports, and declarations match exactly.
  A mismatch can hold up a certification or a customs entry.

## 9. After certification

- [ ] **9.1** The certified configuration is recorded: hardware revision, firmware version, antenna, and power settings.
- [ ] **9.2** Every later change is routed past whoever owns compliance.
  Changes to the radio, antenna, layout around them, or transmit power can mean retesting.
- [ ] **9.3** Test reports, declarations, and the technical file are kept for as long as each market requires.
- [ ] **9.4** For connected products sold in the EU, someone can report an actively exploited vulnerability or severe incident with an early warning within 24 hours.
  The Cyber Resilience Act has required this since September 2026, including for products already on the market.

## Related reading

- [Plan for compliance from day one](https://westlakesys.com/articles/compliance-from-day-one/)
- [Compliance by market: the approvals your product needs](https://westlakesys.com/articles/compliance-by-market/)
- [Compliance planner](https://westlakesys.com/tools/compliance-planner/)
- [Replaceable batteries in the EU: what changes on 18 February 2027](https://westlakesys.com/articles/eu-replaceable-batteries/)
- [EMC pre-scan checklist](https://westlakesys.com/tools/checklists/emc-pre-scan/)
- Next step: [Release to manufacturing checklist](manufacturing-release.md)

---

From [Westlake Systems](https://westlakesys.com/). Licensed under [CC BY 4.0](../LICENSE): reuse and adapt freely, with credit and a link to the original page.
