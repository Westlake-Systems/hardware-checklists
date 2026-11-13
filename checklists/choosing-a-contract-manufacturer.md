# Checklist for choosing a contract manufacturer

What to settle before choosing an electronics contract manufacturer: fit, quotes, parts and inventory, quality and test, ownership, and the first build.

Interactive and printable version: [https://westlakesys.com/tools/checklists/choosing-a-contract-manufacturer/](https://westlakesys.com/tools/checklists/choosing-a-contract-manufacturer/)

What to settle before you choose a contract manufacturer to build your electronics, for teams moving a product toward production. The cheapest quote is often not the cheapest manufacturer once parts, test, and changes are counted.

Choose early if you can. A manufacturer chosen before EVT can review the design while its feedback is still cheap to act on.

## 1. Before you ask for quotes

- [ ] **1.1** Volumes are written down: units per build, expected annual volume, and how firm each number is.
  Manufacturers price and plan around volume, and a quote for 500 units says little about the price at 5,000.
- [ ] **1.2** You know what you are buying: board assembly only, box build, programming and test, packaging, or shipping to customers.
- [ ] **1.3** You know who buys the parts: the manufacturer for every part (turnkey), you for every part (consigned), or a mix.
- [ ] **1.4** The quote package is complete and at one revision, with the BOM, board data, assembly drawing, and quantities, and every manufacturer gets the same package.
  Quotes from an incomplete package carry hidden assumptions, and two manufacturers end up quoting different products.
- [ ] **1.5** An NDA is in place before the package goes out, and it covers anyone the manufacturer shares it with.
- [ ] **1.6** Your cost estimate includes each connector's mating half, cable or harness, and any tooling they need, with their lead times.
  They are often among the most expensive and slowest parts to get, and the easiest to leave out.

## 2. Fit

- [ ] **2.1** The manufacturer builds products like yours at your volumes, wants a project your size, and can grow with you, or you know where production goes if you outgrow it.
  A small project at a large manufacturer can wait behind bigger customers.
- [ ] **2.2** It has the processes your design needs, such as fine-pitch or BGA parts, X-ray inspection, conformal coating, RF test, or secure provisioning of keys, and a solder and cleaning process your parts can take.
  Some parts, such as open-cavity sensors and microphones, are ruined by a wash process.
- [ ] **2.3** It holds the quality certifications your market expects, such as ISO 9001, ISO 13485 for medical devices, IATF 16949 for automotive, or AS9100 for aerospace.
  Check that each certificate is current and covers the site that will build your product.
- [ ] **2.4** No assembly, test, or special process is subcontracted to another site without your approval.
- [ ] **2.5** Location, time zone, language, and shipping and import costs suit how closely you need to work with it.
- [ ] **2.6** You, or someone you trust, have visited the shortlisted manufacturer, seen the line your product would run on, and talked with customers of a similar size.

## 3. The quote

- [ ] **3.1** One-time costs are listed apart from the unit price: setup, stencils, programming, fixtures, and first article inspection.
- [ ] **3.2** Part costs show how they are priced, including any markup, and what is assumed for parts with no quoted price.
- [ ] **3.3** Part overage is addressed: the extra parts the line uses in setup and attrition, minimum order quantities, who pays for the excess, and who owns it after the build.
  A reel bought for ten boards is often charged in full, and a consigned kit counted exactly can stop the line over one resistor.
- [ ] **3.4** Lead time is split into parts, assembly, and test, with the parts that set it named.
- [ ] **3.5** The quote lists its assumptions, exclusions, and payment terms, including any deposit for parts, and how long the prices hold.
- [ ] **3.6** Quotes are compared on total cost at your volume: unit price, one-time costs spread over the volume, excess parts, test, shipping, and duties.

## 4. Engineering support

- [ ] **4.1** A design for manufacturability review is part of quoting or the first order, and its findings come back in writing.
- [ ] **4.2** You have a named contact on the engineering side, not only a buyer or account manager.
- [ ] **4.3** Questions about the package are raised and answered before the build is scheduled, and nothing on the line departs from the package without your written approval.
  Questions that come up while the line is running lead to rushed decisions or guesses.

## 5. Parts and inventory

- [ ] **5.1** Parts are bought from authorized distributors or the part maker, or you approve any other source in advance.
  Brokers can fill shortages, but they carry most of the counterfeit risk; if one is used, ask for traceability and inspection or testing.
- [ ] **5.2** No part is substituted without your written approval, including passives, unless the BOM marks it as open to equivalents.
- [ ] **5.3** Shortages and end-of-life notices are reported to you as soon as the manufacturer learns of them.
- [ ] **5.4** Moisture-sensitive parts are handled to J-STD-033, and consigned parts are tracked so you can see what is held for you.
- [ ] **5.5** Part lot and date codes are traceable to each serial number.
  When a bad batch of parts turns up, this is how you find which units have it.
- [ ] **5.6** Your liability for parts bought against a forecast is written down, including excess and obsolete stock when a forecast changes.

## 6. Quality and test

- [ ] **6.1** The IPC-A-610 acceptance class is agreed, along with the inspection used, such as AOI on every board and X-ray for BGAs and other hidden joints.
  Class 2 suits most products; Class 3 costs more and is for products that must not fail in service.
- [ ] **6.2** The test strategy is agreed: what the manufacturer tests, with which fixture, and to which limits.
- [ ] **6.3** Test results are logged for every serial number, you get the logs, and every build comes with a yield and defect report.
  When yield drops or a unit comes back from the field, those records are how you find out why.
- [ ] **6.4** Failed units have an agreed path: who analyzes them, who pays for repair or scrap, and how corrective actions are reported.
- [ ] **6.5** The flux and cleaning process are agreed, no-clean or washed, and suit any conformal coating and high-impedance circuits on the board.
  Residue left under voltage and humidity can grow conductive paths that leak or short.

## 7. Ownership and terms

- [ ] **7.1** The agreement lists the fixtures, stencils, and programming hardware you pay for as customer-owned, and you hold the design files and software for them.
  Paying a tooling charge does not always make the tooling yours. Without it, moving production or fixing the test means starting over.
- [ ] **7.2** The agreement covers engineering changes: how they are priced and scheduled, and what happens to stock and units in progress.
- [ ] **7.3** A workmanship warranty is in writing: how long it lasts, and who pays for rework, scrap, and field returns caused by assembly errors, parts included.
  Standard terms often limit the manufacturer to the cost of its own labor, leaving you to pay for the parts on scrapped boards.
- [ ] **7.4** You know how you would leave: how fixtures, inventory, and files come back to you if you move production.

## 8. The first build

- [ ] **8.1** The first build is small, and first article sign-off is agreed in advance: who approves it, on site or remotely, and whether the line waits.
  A line held while someone approves remotely costs time and money, so settle it before the build.
- [ ] **8.2** Someone from your side is on site or on call during the first build to answer questions quickly.
- [ ] **8.3** The manufacturer sends a build report covering defects, yield, questions raised, and any deviations from the package.

## Related reading

- [Release to manufacturing checklist](https://westlakesys.com/tools/checklists/manufacturing-release/)
- [What a complete manufacturing package includes](https://westlakesys.com/articles/manufacturing-package/)
- [From prototype to production: EVT, DVT, and PVT explained](https://westlakesys.com/articles/prototype-to-production/)
- [Designing for production test](https://westlakesys.com/articles/designing-for-production-test/)
- Next step: [EVT, DVT, and PVT exit checklist](evt-dvt-pvt.md)

---

From [Westlake Systems](https://westlakesys.com/). Licensed under [CC BY 4.0](../LICENSE): reuse and adapt freely, with credit and a link to the original page.
