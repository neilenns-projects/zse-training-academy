---
title: Weather observations and forecasts
description: Overview of weather and its applicability to air traffic control.
weight: 40
---

Weather is extremely important for aviation, and controllers need to know how to read weather reports and understand how the weather will impact operations.

The real world ZSE ARTCC produces a regular [pre-duty weather briefing](https://www.weather.gov/zse/PDWBsite) which is a helpful summary of current weather affecting ATC.

For details on these topics and much more, see the [vZAB seminar on aviation weather](https://www.youtube.com/watch?v=KvJT2PQBDtc).

## Notes about units

When working with weather you'll encounter many measurements, including heights and headings. Depending on the context the reference for the values may be different.

METAR/TAF clouds are in **AGL** (above ground level).

METAR/TAF winds are in **true** heading, however flying is done with **magnetic** heading. In ZSE, **subtract 20** from the true wind heading to get the magnetic wind heading.

> [!TIP]
> If you read it, it's true. If you hear it, it's magnetic.
