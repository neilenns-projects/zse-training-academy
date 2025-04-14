---
title: Airways
description: Overview of airway types and ensure aircraft are flying the correct ones.
weight: 80
---

Airways provide a standard set of routes for aircraft to follow that help maintain a safe and orderly flow of traffic. Non-RNAV routes also ensure the ability to navigate based on [VORs](https://www.faa.gov/about/office_org/headquarters_offices/ato/service_units/techops/navservices/gbng/vor).

There are two types of airways based on altitude, and two classifications of each type. ([7110.65 2-5](https://www.faa.gov/air_traffic/publications/atpubs/atc_html/chap2_section_5.html)).

## Low-altitude airways

Low-altitude airways cover from 1200' AGL, up to but not including FL180. Use the SkyVector **[World Lo](https://skyvector.com/?ll=46.04604009236032,-121.42529297089746&chart=302&zoom=5&fpl=undefined)** map to see low-altitude airways. The airways are pronounced using the phonetic alphabet ([7110.65 2-5-1](https://www.faa.gov/air_traffic/publications/atpubs/atc_html/chap2_section_5.html)).

Victor airways (**V**) are depicted in black on charts. They rely on NAVAIDs and use non-RNAV routing.

{{< figure src="v120.png" alt="Section of a chart depicting V120." caption="Low-altitude airway V120, pronounced \"**victor one twenty**\"" >}}

Tango routes (**T**) are depicted in blue on charts. They are RNAV routes and do not rely on NAVAIDs.

{{< figure src="t317.png" alt="Section of a chart depicting T317." caption="Low-altitude route T317, pronounced \"**tango three seventeen**\"" >}}

### V/T minimum altitudes

Low-altitude airways have a Minimum Enroute Altitude (**MEA**). The MEA is the lowest altitude an aircraft should be at on any airway. This ensures reception of NAVAIDs, two-way radio communication with ATC, and appropriate terrain and obstruction clearance.

Any altitude listed on the chart without additional text is the MEA. An altitude in blue with a G at the end provides an alternative MEA for aircraft using GPS to navigate the airway.

Any altitude listed with an asterisk (\*) next to it indicates the Minimum Obstruction Clearance Altitude (**MOCA**). A MOCA is the lowest altitude in effect on an airway which ensures terrain and obstruction clearance. These altitudes should not be assigned except as permitted in [7110.65 4-5-6](https://www.faa.gov/air_traffic/publications/atpubs/atc_html/chap4_section_5.html#HHJ168JACK).

In the following example:

- the MEA is 14000' MSL for flights heading to the left.
- the MEA is 12000' MSL for flights heading to the right.
- if the airway is being flown with GPS, the MEA is 11000' MSL, shown in blue with the G.
- the MOCA is 11000' MSL for both directions.
- the distance for this segment is 11 NM.
- the SEDTO intersection is 36 NM from the navaid to the right.

{{< figure src="v165.png" alt="Section of a chart depicting V165." caption="V165 MEAs" >}}

> [!TIP]
> When verifying flight plans ensure the filed altitude meets the MEA for all segments of the route. This is typically an issue with small aircraft making short flights, for example between KPDX and KYKM.
>
> Flights flying at or above FL180 should not include low-altitude airways in their flight plan.

## High-altitude airways

High-altitude airways cover FL180 up to and including FL450. Use SkyVector **[World Hi](https://skyvector.com/?ll=46.04604008800145,-121.42529296802381&chart=304&zoom=3&fpl=undefined)** map to see high-altitude airways.

The airways are pronounced using the letters by their name ([7110.65 2-5-1](https://www.faa.gov/air_traffic/publications/atpubs/atc_html/chap2_section_5.html)).

**J** airways are depicted in black on charts. The jet route or jet airway system has set established routes starting from 18,000 MSL up to and including FL450. They use non-RNAV routing.

{{< figure src="j70.png" alt="Section of a chart depicting J70." caption="High-altitude airway J70, pronounced \"**jay seventy**\"" >}}

**Q** routes are depicted in blue on charts. These are for use by RNAV aircraft between 18,000 MSL up to and including FL450.

{{< figure src="q144.png" alt="Section of a chart depicting Q144." caption="High-altitude route Q144, pronounced \"**queue one forty-four**\"" >}}

[**Y** routes](https://www.faa.gov/air_traffic/publications/atpubs/aip_html/part2_enr_section_7.10.html#ByAU9119cchgh) are another type of RNAV airway. Most of these routes are in high-altitude offshore airspace in the southeast; none of them are near ZSE. Aircraft must have GNSS to use these airways.

### J/Q minimum altitudes

The MEA on any high-altitude airways is 18000' MSL, unless otherwise stated. Aircraft flying between 18000' MSL and FL450 are allowed to navigate via these airways.

High-altitude airways are less likely to have alternate altitude limits; however, they may be listed on the chart. In the following example:

- the MEA is 19000' MSL that is in effect from 1100 to 0300Z.
- it has a Maximum Authorized Altitude (**MAA**) of 29000' MSL.

{{< figure src="j30-34.png" alt="Section of a chart depicting J30-34." caption="J30-34 MEA" >}}

> [!TIP]
> When verifying flight plans ensure the filed altitude is at least 18000' MSL if the route includes high-altitude airways. This is not a common issue on the network.
