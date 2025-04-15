---
title: Equipment suffixes
description: Overview of FAA equipment suffixes and how they apply to S1 tasks.
weight: 60
---

<!-- markdownlint-disable MD028 -->
Equipment suffixes ([7110.65 2-3-9](https://www.faa.gov/air_traffic/publications/atpubs/atc_html/chap2_section_3.html#$paragraph2-3-9)) are used to indicate the navigation capabilities of an aircraft. The suffix is added to the aircraft's call sign in the flight plan and is used by air traffic control to determine the appropriate separation and routing for the aircraft.

The suffixes are as follows:

<!-- The table is raw HTML, so moved to a shortcode to prevent markdownlint errors
and problems with prettier auto-formatting of the file. -->
{{< equipment-suffixes >}}

You do not need to memorize all of them, but it's expected that you know the most common ones found on VATSIM. Since all aircraft on VATSIM have a Mode C transponder, the suffixes highlighted in green above are the only ones used: **/L**, **/G**, **/A**, **/W**, **/Z**, **/U**, **/P**, and **/I**.

> [!NOTE]
> **/P** is for military fighter jets. **/I** is the same as **/W**; however, flights are restricted to altitudes below FL290. Neither are common on VATSIM.

### Common equipment suffixes

As a clearance delivery controller, it is your responsibility to understand how each suffix affects what the aircraft can fly. When validating a flight plan, use the equipment suffix to evaluate the aircraft's **navigation** and **RVSM** capability.

| Suffix | Description                                     | Notes                                                                                                                                                                                                                                           |
| ------ | ----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| /L     | RVSM, GNSS, transponder with Mode C             | **Capable of FL290 or above, has GPS**. Most modern airliners are in this category.                                                                                                                                                             |
| /G     | No RVSM, GNSS, transponder with Mode C          | **Restricted to flights below FL290, has GPS**. This is common for smaller planes with modern avionics like the Cessna 172 with the G1000 glass cockpit.                                                                                        |
| /A     | No RVSM, DME, transponder with Mode C           | **Restricted to flights below FL290¹, navigation by VOR/DME capability** This is common for smaller planes without GPS, like the Cessna 152 with analog gauges.                                                                                 |
| /W     | RVSM, No RNAV, No GNSS, transponder with Mode C | **Capable of FL290 or above, navigation by VOR/DME capability.** This is common for older airliners without RNAV.                                                                                                                               |
| /Z     | RVSM, RNAV, No GNSS, transponder with Mode C    | **Capable of FL290 or above, basic RNAV (i.e. INS, may be able to use RNAV SIDs or STARs), and VOR/DME**. This is common for older airliners that don't have GPS, but have an IRU that still allows them to navigate with some RNAV capability. |

> [!TIP]
> For equipment codes restricted to flights below FL290 (no RVSM), it is easiest to ask the pilot to fly at an altitude below FL290. If the pilot insists on flying at or above FL290, coordinate with the En-Route controller.

> [!NOTE]
> [RNAV can get complicated](https://www.faa.gov/air_traffic/publications/atpubs/aim_html/chap1_section_2.html). INS is very precise, but its accuracy drifts over time. It needs another navigation system to provide corrections. GPS is one possible source of these corrections, but another source could be DME. FAA equipment codes don't get into more detailed capabilities like this, but [ICAO equipment codes do](https://en.wikipedia.org/wiki/Equipment_codes).

## Equipment suffixes in practice

The most common issues related to suffixes on the network are:

- modern airliners filing a suffix other than /L.
- missing suffixes.
- piston aircraft filing something other than /A or /G.
- older aircraft with uncommon suffixes, such as /Z or /W.

### Example 1

A pilot files this flight plan. What should you do?

{{< fpe aid="ASA914" typ="B738" eq="X" dep="KPDX" dest="KSFO" spd="500" alt="350" rte="MINNE5 FAMUK Q3 FOWND MLBEC BDEGA4" rmk="RMK/TCAS SIMBRIEF" >}}

{{% details title="Show answer" closed="true" %}}

Just correct it to **/L** in the flight plan. This happens so often on the network it is not worth the time spent on frequency asking the pilot for the correct suffix.

{{% /details %}}

### Example 2

A pilot files this flight plan. What should you do?

{{< fpe aid="N6966S" cid="1923432" typ="C152" eq="" dep="KPDX" dest="KSEA" spd="090" alt="060" rte="BTG V23 SEA" rmk="NEW PILOT" >}}

{{% details title="Show answer" closed="true" %}}

Ask the pilot for clarification, since piston aircraft could be either **/A** or **/G**.

{{< audio src="example2.mp3" >}}

{{< pilot callsign="N6966S" >}}
Portland Ground, N6966S. Requesting IFR to KSEA.
{{< /pilot >}}

{{< controller callsign="Portland Ground" >}}
N6966S, Portland Ground, good morning. What is your equipment suffix?
{{< /controller >}}

{{< pilot callsign="N6966S" >}}
We're a Cessna 152.
{{< /pilot >}}

{{< controller callsign="Portland Ground" >}}
Do you have a GPS onboard? Or just the analog gauges?
{{< /controller >}}

{{< pilot callsign="N6966S" >}}
We have a GPS.
{{< /pilot >}}

{{< controller callsign="Portland Ground" >}}
Ok, your suffix is slant golf. I'll update your flight plan for you.
{{< /controller >}}

Then update the flight plan with the suffix, and clear the pilot as normal.

{{% /details %}}

### Example 3

A pilot files this flight plan. What should you do?

{{< fpe aid="N4940G" typ="C172" eq="L" dep="KPDX" dest="KSEA" spd="090" alt="060" rte="BTG V23 SEA" >}}

{{% details title="Show answer" closed="true" %}}

Ask the pilot for clarification, since piston aircraft could be either **/A** or **/G**.

{{< pilot callsign="N4940G" >}}
Portland Ground, N4940G, good morning, requesting IFR to Seattle. We have information delta.
{{< /pilot >}}

{{< controller callsign="Portland Ground" >}}
N4940G, Portland Ground, good morning. What is your equipment suffix? You filed slant lima, which probably isn't right for a Cessna 172.
{{< /controller >}}

{{< pilot callsign="N4940G" >}}
We're slant golf. Sorry about that!
{{< /pilot >}}

Then update the flight plan with the suffix, and clear the pilot as normal.

{{% /details %}}

### Example 4

A pilot files the following flight plan. What should you do?

{{< fpe aid="PNW42" typ="B742" eq="W" dep="KPDX" dest="CYVR" spd="300" alt="340" rte="BTG V287 OLM V165 HUH V23 YVR" rmk="CS=TIMBERLINE / NO RNAV SIDS" >}}

{{% details title="Show answer" closed="true" %}}

The equipment suffix is likely correct since the 747-200 is an older airplane, and the pilot explicitly stated in remarks that RNAV SIDs cannot be accepted. This indicates the pilot knows the capabilities of their plane, and used the correct suffix.

Make no changes to the filed equipment suffix; however, pay close attention to the SID and STAR when reviewing the route for accuracy before issuing a clearance.

> [!TIP]
> Pacific Northwest Airways is a virtual airlines based in the northwest. `PNW` is `TIMBERLINE` when spoken on frequency.

{{% /details %}}
