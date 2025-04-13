---
title: Cruise altitude assignment
description: Overview of cruise altitudes and how to assign them correctly to aircraft.
weight: 70
---

> [!NOTE]
> Knowledge of this section is required to pass 2.1.1b on the S1 rating examination.

IFR flight plans require a filed altitude that is correct based on the direction of flight. The direction of flight is determined by the straight line between the departure and arrival airports, and the heading is the **magnetic** heading of the flight. [SkyVector](https://www.skyvector.com/) is a convenient website to visualize the direction of flight for an airport pair.

The following table shows the correct altitudes for each direction of flight ([7110.65 4-5-2](https://www.faa.gov/air_traffic/publications/atpubs/atc_html/chap4_section_5.html#N6M50JACK)). Rows in green indicate the most common situations on VATSIM.

<!-- Markdown tables don't support coloured rows, so use raw HTML to get a good looking table. -->
<!-- markdownlint-disable MD033 -->

<table>
  <thead>
    <tr>
      <th>Aircraft operating</th>
      <th>On course degrees magnetic</th>
      <th>Assign</th>
      <th>Examples</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Below 3,000 feet above surface</td>
      <td>Any course</td>
      <td>Any altitude</td>
      <td>3,000, 5,000, FL 310, FL 330</td>
    </tr>
    <tr class="vatsim-supported">
      <td>At and below FL 410</td>
      <td>0 through 179</td>
      <td>Odd cardinal altitude or flight levels at intervals of 2,000 feet</td>
      <td>3,000, 5,000, FL 310, FL 330</td>
    </tr>
    <tr class="vatsim-supported">
      <td>At and below FL 410</td>
      <td>180 through 359</td>
      <td>Even cardinal altitude or flight levels at intervals of 2,000 feet</td>
      <td>4,000, 6,000, FL 320, FL 340</td>
    </tr>
    <tr class="vatsim-supported">
      <td>Above FL 410</td>
      <td>0 through 179</td>
      <td>Odd cardinal flight levels at intervals of 4,000 feet beginning with FL 450</td>
      <td>FL 450, FL 490, FL 530</td>
    </tr>
    <tr class="vatsim-supported">
      <td>Above FL 410</td>
      <td>180 through 359</td>
      <td>Even cardinal flight levels at intervals of 4,000 feet beginning with FL 430</td>
      <td>FL 430, FL 470, FL 510</td>
    </tr>
    <tr>
      <td>One way routes (except in composite systems)</td>
      <td>Any course</td>
      <td>Any cardinal altitude or flight level below FL 410 or any odd cardinal flight level above FL 410</td>
      <td>FL 270, FL 280, FL 290, FL 300, FL 310, FL 410, FL 430, FL 450</td>
    </tr>
    <tr>
      <td>Within an ALTRV</td>
      <td>Any course</td>
      <td>Any altitude or flight level</td>
      <td>—</td>
    </tr>
    <tr>
      <td>In aerial refueling tracks and anchors</td>
      <td>Any course</td>
      <td>Altitude blocks as requested. Any altitude or flight level</td>
      <td>050B080, FL 180B220, FL 280B310</td>
    </tr>
  </tbody>
</table>

<!-- markdownlint-enable MD033 -->

## RVSM airspace

RVSM is the reduction of required vertical separation between aircraft from 2,000 to 1,000 feet, starting at FL290 and up to FL410, inclusive. In this airspace, aircraft are separated vertically by 1,000 feet instead of the normal 2,000 feet. This means that aircraft must be [RVSM capable](/developing-s1/equipment-suffixes/) to operate in this airspace, unless prior approval from the en-route controller is obtained.

> [!NOTE]
> Not all aircraft are RVSM capable. When verifying flight plans, you should check the equipment suffix to see if the aircraft is RVSM capable and confirm the filed altitude is allowed.

## Lowest usable flight level

The lowest usable flight level may vary based on the local altimeter setting.

If the current atmospheric pressure affects the usable flight level in your area of jurisdiction, use the following table to determine the lowest usable flight level to clear aircraft at or above 18,000 feet MSL. [(7110.65 4-5-4)](https://www.faa.gov/air_traffic/publications/atpubs/atc_html/chap4_section_5.html#$paragraph4-5-4).

| Altimeter setting | Lowest usable flight level |
| ----------------- | :------------------------: |
| 29.92 or higher   |            180             |
| 29.91 to 28.92    |            190             |
| 28.91 to 27.92    |            200             |

Practically speaking, sea level pressures below 28.92 are not common, so FL180 is the level you want to pay the most attention to unless the pressure is unusually low.

> [!TIP]
> FL180 is most common on flight plans when pilots fly between nearby airports, for example between KPDX and KSEA.

## Cruise altitude assignment in practice

The most common mistakes with filed cruise altitudes are:

- wrong altitude for the direction of flight within RVSM altitudes.
- incorrect altitudes for flights above RVSM altitudes.
- non-RVSM aircraft filing an RVSM altitude.
- shorter flights filing FL180, when the altimeter setting is below 29.92.

When you receive a flight plan, check the filed altitude against the direction of flight and the aircraft's [equipment suffix](/developing-s1/equipment-suffixes/). If the filed altitude is incorrect, you should inform the pilot and offer them a new altitude that is correct for their flight.

### Example 1

A B738/L files a flight from KPDX to CYVR at **FL310**. What should you do?

{{% details title="Show answer" closed="true" %}}

The B738 is RVSM capable, however the [direction of flight between KPDX and CYVR is 339°](https://skyvector.com/?fpl=KPDX%20CYVR) so the cruise altitude should be even.

{{< pilot callsign="WJA123" >}}
Portland Ground, WJA123, requesting IFR to Vancouver. We have information delta.
{{< /pilot >}}

{{< controller callsign="Portland Ground" >}}
WJA123, Portland Ground, your filed altitude of flight level 310 is unavailable. Would you like flight level 300 or 320?
{{< /controller >}}

{{< pilot callsign="WJA123" >}}
We'll take flight level 300.
{{< /controller >}}

Then update the flight plan with the new altitude and clear the pilot as normal.

{{% /details %}}

### Example 2

A C700/L files a flight from KPDX to KJFK at **FL460**. What should you do?

{{% details title="Show answer" closed="true" %}}

The C700 is RVSM capable; however, the filed flight level is above RVSM altitudes and FL460 is a westbound altitude. The [direction of flight between KPDX and KJFK is 65°](https://skyvector.com/?fpl=KPDX%20KJFK).

{{< pilot callsign="N10GE" >}}
Portland Ground, N10GE, requesting IFR to JFK. We have information delta.
{{< /pilot >}}

{{< controller callsign="Portland Ground" >}}
N10GE, Portland Ground, your filed altitude of flight level 460 is unavailable. Can you do flight level 450?
{{< /controller >}}

{{< pilot callsign="N10GE" >}}
450 is fine.
{{< /pilot >}}

Then update the flight plan with the new altitude and clear the pilot as normal.

{{% /details %}}

### Example 3

A DH8D/G files a flight from KSEA to KPDX at **FL290**. What should you do?

{{% details title="Show answer" closed="true" %}}

The DH8D is not RVSM capable, so it cannot file an altitude at or above FL290. The [direction of flight between KSEA and KPDX is 171°](https://skyvector.com/?fpl=KSEA%20KPDX), so the cruise altitude should be odd.

{{< pilot callsign="QXE123" >}}
Portland Ground, QXE123, requesting IFR to Portland. We have information delta.
{{< /pilot >}}

{{< controller callsign="Portland Ground" >}}
QXE123, Portland Ground, your filed altitude of flight level 290 is unavailable. Can you do flight level 270?
{{< /controller >}}

{{< pilot callsign="QXE123" >}}
That'll work
{{< /pilot >}}

Then update the flight plan with the new altitude and clear the pilot as normal.

Alternatively, you can coordinate with the en-route controller to see if they can accept the flight at FL290. In practice this is far more work for both you and the en-route controller, so it is simpler and faster to assign a non-RVSM altitude.

{{% /details %}}

### Example 4

A C25C/L files **FL180** for a flight from KPDX to KSEA. The current altimeter is 29.90. What do you do?

{{% details title="Show answer" closed="true" %}}

The filed altitude is below the lowest usable flight level, which is **FL190**. The [direction of flight between KPDX and KSEA is 351°](https://skyvector.com/?fpl=KSEA%20KPDX), so the cruise altitude must be even.

{{< pilot callsign="N10GE" >}}
Portland Ground, N10GE, requesting IFR to Seattle. We have information delta.
{{< /pilot >}}

{{< controller callsign="Portland Ground" >}}
N10GE, Portland Ground, your filed altitude of flight level 180 is unavailable. Can you do 16,000?
{{< /controller >}}

{{< pilot callsign="N10GE" >}}
Can we do FL200?
{{< /pilot >}}

{{< controller callsign="Portland Ground" >}}
Sure thing.
{{< /controller >}}

Then update the flight plan with the new altitude and clear the pilot as normal.

{{% /details %}}
