# Hardware engineering checklists

Checklists for electronics hardware projects, from hiring a design firm and reviewing a schematic to bring-up, EMC, certification, and the builds on the way to production.

These are the checks Westlake Systems works through on its own projects, plus a few written to help with decisions around them, such as hiring a design firm. Each one is also on [westlakesys.com](https://westlakesys.com/tools/), where you can tick items off on screen or print a copy to mark up at the bench or in a review.

## Checklists

<!-- checklists:start -->
- [Checklist for hiring a hardware design firm](checklists/hiring-a-design-firm.md): What to settle before you hire an outside firm or contractor for electronics design: scope, deliverables, ownership, process, cost, and production.
- [Schematic and layout review checklist](checklists/design-review.md): What to check in a schematic and board layout before you order boards: power, parts, clocks, RF, layout, EMC, thermal, DFM, test access, and release.
- [Antenna and RF integration checklist](checklists/antenna-integration.md): How to get a radio and antenna working in a real product: requirements, antenna choice, placement, matching, testing, coexistence, and production.
- [UWB design review checklist](checklists/uwb-design-review.md): Checks for an ultra-wideband ranging or positioning design: requirements, regulation, link budget, antenna, layout, calibration, firmware, and test.
- [First board bring-up checklist](checklists/board-bring-up.md): How to bring up a new board safely and learn the most from it: preparation, inspection, first power, clocks, debug, peripherals, RF, and power.
- [Checklist for choosing a contract manufacturer](checklists/choosing-a-contract-manufacturer.md): What to settle before choosing an electronics contract manufacturer: fit, quotes, parts and inventory, quality and test, ownership, and the first build.
- [EVT, DVT, and PVT exit checklist](checklists/evt-dvt-pvt.md): What each hardware build should prove before the next: planning, EVT, DVT, and PVT exit criteria, design freeze, and the review after every build.
- [Release to manufacturing checklist](checklists/manufacturing-release.md): What to include and confirm before releasing a design to a board fab and contract manufacturer: data, BOM, programming, test, labels, and revisions.
- [EMC pre-scan checklist](checklists/emc-pre-scan.md): How to run an in-house EMC pre-scan before formal testing: setup, near-field scans, radiated and conducted emissions, ESD, and fixes.
- [Compliance readiness checklist](checklists/compliance-readiness.md): What to settle before you book a compliance test lab: markets and standards, radio approach, design checks, pre-scans, test modes, samples, and paperwork.
<!-- checklists:end -->

## Related reading

Articles on westlakesys.com that go with the checklists:

- [Why UWB range falls short of the datasheet](https://westlakesys.com/articles/uwb-range/)
- [Adding a PA or an LNA to a UWB design](https://westlakesys.com/articles/uwb-pa-lna/)
- [UWB antenna delay calibration: what it is and how to do it](https://westlakesys.com/articles/uwb-antenna-delay/)
- [Good return loss, poor ranging: group delay in UWB antennas](https://westlakesys.com/articles/uwb-group-delay/)
- [UWB transmit power: what the limits actually say](https://westlakesys.com/articles/uwb-transmit-power-limits/)
- [An AI tool designed your board. What to check before you order it](https://westlakesys.com/articles/ai-designed-board-before-you-order/)
- [What I look for in a hardware design review](https://westlakesys.com/articles/design-review/)
- [More articles](https://westlakesys.com/articles/)

## Using them

The files are plain Markdown with GitHub task lists, so you can copy a checklist into an issue, a pull request, or your own project docs and tick items off there.

The checklists are generated from the source of the website, so changes are made there and published here. Suggestions and corrections are welcome as issues.

## License

[CC BY 4.0](LICENSE). You may copy, adapt, and share these checklists, including commercially, as long as you credit Westlake Systems and link to the original page.
