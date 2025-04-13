---
title: Aircraft navigation basics
description: Overview of equipment suffixes, RVSM airspace, direction of flight altitude rules, and lowest usable flight levels.
weight: 50
---

This page covers important topics related to aircraft navigation:

- Equipment suffixes ([7110.65 2-3-9](https://www.faa.gov/air_traffic/publications/atpubs/atc_html/chap2_section_3.html#$paragraph2-3-9))
- RVSM Airspace ([7110.65 4-5-1](https://www.faa.gov/air_traffic/publications/atpubs/atc_html/chap4_section_5.html))
- Altitudes based on the direction of flight ([7110.65 4-5-2](https://www.faa.gov/air_traffic/publications/atpubs/atc_html/chap4_section_5.html#N6M50JACK)
- Lowest Usable Flight Level ([7110.65 4-5-4](https://www.faa.gov/air_traffic/publications/atpubs/atc_html/chap4_section_5.html#$paragraph4-5-4))

## Equipment suffixes

Equipment suffixes are used to indicate the navigation capabilities of an aircraft. The suffix is added to the aircraft's call sign in the flight plan and is used by air traffic control to determine the appropriate separation and routing for the aircraft.

The suffixes are as follows:

<!-- Markdown tables don't support merged rows/columns, so use raw HTML to get a good looking table. -->
<!-- markdownlint-disable MD033 -->
<table>
  <thead>
    <tr>
      <th>Separation Standard</th>
      <th>Navigation Capability</th>
      <th>Transponder Capability</th>
      <th>Suffix</th>
    </tr>
  </thead>
  <tbody>
    <tr><td rowspan="5">RVSM</td><td>Any</td><td>Failed transponder</td><td>/H</td></tr>
    <tr><td>Any</td><td>Failed Mode C</td><td>/O</td></tr>
    <tr class="vatsim-supported"><td>No RNAV, No GNSS</td><td>Transponder with Mode C</td><td>/W</td></tr>
    <tr class="vatsim-supported"><td>RNAV, No GNSS</td><td>Transponder with Mode C</td><td>/Z</td></tr>
    <tr class="vatsim-supported"><td>GNSS</td><td>Transponder with Mode C</td><td>/L</td></tr>
    <tr><td rowspan="15">Non-RVSM</td><td></td><td>No transponder</td><td>/X</td></tr>
    <tr><td>No DME</td><td>Transponder, no Mode C</td><td>/T</td></tr>
    <tr class="vatsim-supported"><td>No DME</td><td>Transponder with Mode C</td><td>/U</td></tr>
    <tr><td>DME</td><td>No transponder</td><td>/D</td></tr>
    <tr><td>DME</td><td>Transponder, no Mode C</td><td>/B</td></tr>
    <tr class="vatsim-supported"><td>DME</td><td>Transponder with Mode C</td><td>/A</td></tr>
    <tr><td>TACAN</td><td>No transponder</td><td>/N</td></tr>
    <tr><td>TACAN</td><td>Transponder, no Mode C</td><td>/M</td></tr>
    <tr class="vatsim-supported"><td>TACAN</td><td>Transponder with Mode C</td><td>/P</td></tr>
    <tr><td>RNAV, No GNSS</td><td>No transponder</td><td>/Y</td></tr>
    <tr><td>RNAV, No GNSS</td><td>Transponder, no Mode C</td><td>/C</td></tr>
    <tr class="vatsim-supported"><td>RNAV, No GNSS</td><td>Transponder with Mode C</td><td>/I</td></tr>
    <tr><td>GNSS</td><td>No transponder</td><td>/V</td></tr>
    <tr><td>GNSS</td><td>Transponder, no Mode C</td><td>/S</td></tr>
    <tr class="vatsim-supported"><td>GNSS</td><td>Transponder with Mode C</td><td>/G</td></tr>
  </tbody>
</table>
<!-- markdownlint-enable MD033 -->

You do not need to memorize all of them, but it's expected that you know the most common ones found on VATSIM. Since all aircraft on VATSIM have a Mode C transponder, the suffixes highlighted in green above are the only ones used: **/L**, **/G**, **/A**, **/W**, **/Z**, **/U**, **/P**, and **/I**.

> [!NOTE]
> **/P** is for military fighter jets, and **/I** is the same as /W however flights are restricted to altitudes below FL290. Neither are common on VATSIM.

As a clearance delivery controller, it is also your responsibility to know what the different types of equipment suffixes are and how each one affects what the aircraft can fly. When validating a flight plan use the equipment suffix to take into account the aircraft's **navigation** and **RVSM** capability.

### Common equipment suffixes

| Suffix | Description                                     | Notes                                                                                                                                                                                                                                           |
| ------ | ----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| /L     | RVSM, GNSS, transponder with Mode C             | **Capable of FL290 or above, has GPS**. Most modern airliners are in this category.                                                                                                                                                             |
| /G     | No RVSM, GNSS, transponder with Mode C          | **Restricted to flights below FL290, has GPS**. This is common for smaller planes with modern avionics like the Cessna 172 with the G1000 glass cockpit.                                                                                        |
| /A     | No RVSM, DME, transponder with Mode C           | **Restricted to flights below FL290¹, navigation by VOR/DME capability** This is common for smaller planes without GPS like the Cessna 152 with analog gauges.                                                                                  |
| /W     | RVSM, No RNAV, No GNSS, transponder with Mode C | **Capable of FL290 or above, navigation by VOR/DME capability.** This is common for older airliners without RNAV.                                                                                                                               |
| /Z     | RVSM, RNAV, No GNSS, transponder with Mode C    | **Capable of FL290 or above, basic RNAV (i.e. INS, may be able to use RNAV SIDs or STARs), and VOR/DME**. This is common for older airliners that don't have GPS, but have an IRU that still allows them to navigate with some RNAV capability. |

<!-- Markdownlint doesn't like consecutive GitHub callout boxes. >
<!-- markdownlint-disable MD028 -->
> [!TIP]
> For equipment codes restricted to flights below FL290 (no RVSM), if the pilot wants to fly above FL290, coordinate with the En-Route controller.

> [!NOTE]
> [RNAV can get complicated](https://www.faa.gov/air_traffic/publications/atpubs/aim_html/chap1_section_2.html). INS is very precise but its accuracy drifts over time, so it needs another navigation system to provide corrections. GPS is one possible source of these corrections, but another source could be DME. FAA equipment codes don't get into more detailed capabilities like this, but [ICAO equipment codes do](https://en.wikipedia.org/wiki/Equipment_codes).
<!-- markdownlint-enable MD028 -->