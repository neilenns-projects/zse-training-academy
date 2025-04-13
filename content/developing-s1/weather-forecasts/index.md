---
title: Weather forecasts
description: Overview of weather forecasts and their application to air traffic control.
weight: 40
---

Weather is extremely important for aviation, and controllers need to know how to read weather reports and understand how the weather will impact operations.

The real world ZSE ARTCC produces a regular [pre-duty weather briefing](https://www.weather.gov/zse/PDWBsite) which is a helpful summary of current weather affecting ATC.

For details on these topics and much more, see the [vZAB seminar on aviation weather](https://www.youtube.com/watch?v=KvJT2PQBDtc).

## Understanding weather measurements

When dealing with aviation weather data, you'll come across various measurements like altitudes and wind directions. It's important to know what each value is relative to, as it can change depending on the source.

METAR/TAF clouds are in **AGL** (above ground level).

METAR/TAF winds are in **true** heading; however, flying is done with **magnetic** heading. In ZSE, **subtract 20°** from the true wind heading to get the magnetic wind heading. The number of degrees to add or subtract will vary by ARTCC.

> [!TIP]
> When giving wind information to pilots, it will always be in **magnetic** heading. On VATSIM, a text communication with a pilot such as a text ATIS or message to a text-only pilot is considered voice, and the wind will be in **magnetic** heading.
>
> A common mantra to remember this is: "If you read it, it's true. If you hear it, it's magnetic."

## Flight rule minimums

For aircraft to fly at an airport under Visual Flight Rules (VFR), the weather must meet [specific minimums](https://www.ecfr.gov/current/title-14/chapter-I/subchapter-F/part-91/subpart-B/subject-group-ECFR4d5279ba676bedc/section-91.155#p-91.155%28c%29): 3 miles visibility and 1000 foot ceilings. The [ceiling](https://www.ecfr.gov/current/title-14/chapter-I/subchapter-A/part-1/section-1.1#p-1.1%28Ceiling%29) is defined as the lowest **broken (BKN)** or **overcast (OVC)** layer.

If the visibility is [at least 1 mile](https://www.ecfr.gov/current/title-14/chapter-I/subchapter-F/part-91#91.157), airplanes may request [**Special VFR (SVFR)**](https://www.faa.gov/air_traffic/publications/atpubs/atc_html/chap7_section_5.html) to enter or depart the airport area.

## METAR

METeorological Aerodrome Reports (METARs) typically come from airports. Reports are generated once an hour, but if conditions change significantly at a staffed location, a report known as a special (SPECI) may be issued.
A typical METAR contains data for the temperature, dew point, wind direction, and speed, precipitation, cloud cover and heights, visibility, and barometric pressure. A METAR may also contain information on precipitation amounts, lightning, and other information that would be of interest to pilots or meteorologists such as a pilot report or PIREP, color states, and runway visual range (RVR).

METARs and TAFs have many [abbreviations and acronyms](https://www.weather.gov/media/wrh/mesowest/metar_decode_key.pdf). Another helpful site is [metar-taf.com](https://metar-taf.com) which provides a plain text description and graphical depiction of the conditions in the METAR and TAF.

Here is an example METAR from Hillsboro, Oregon (KHIO):

```plaintext
METAR KHIO 192253Z 12012KT 10SM SCT019 BKN055 09/04 A2966 RMK AO2 SLP044 T00890044
```

Each item of the METAR is decoded as follows:

| Item      | Description                                                             |
| --------- | ----------------------------------------------------------------------- |
| KHIO      | The station identifier (Hillsboro Airport)                              |
| 192253Z   | The date and time of the report (19th day of the month at 22:53 UTC)    |
| 12012KT   | Wind from 120 degrees at 12 knots (in true heading)                     |
| 10SM      | Visibility of 10 statute miles                                          |
| SCT019    | Scattered clouds at 1900 feet AGL                                       |
| BKN055    | Broken clouds at 5500 feet AGL                                          |
| 09/04     | Temperature of 9 degrees Celsius and dew point of 4 degrees Celsius     |
| A2966     | Altimeter setting of 29.66 inches of mercury                            |
| RMK AO2   | Remarks indicating the station is automated with precipitation sensor   |
| SLP044    | Sea-level pressure of 1004.4 hPa                                        |
| T00890044 | Temperature of 8.9 degrees Celsius and dew point of 4.4 degrees Celsius |

> [!NOTE]
> Items after the `RMK` field are not always present. Decoding items after the `RMK` field is not required for the S1 ratings examination.

## TAF

Terminal Area Forecasts (TAFs) are issued at least four times a day, every six hours, for major civil airfields: 0000, 0600, 1200 and 1800 UTC, and generally apply to a 24- or 30-hour period, and an area within approximately five statute miles from the center of an airport runway complex. Not all airports with a METAR will have a TAF.

Here is an example TAF taken from KHIO:

```plaintext
KHIO 192323Z 2000/2024 12011KT P6SM BKN060
FM200500 09004KT P6SM SCT025
FM201400 VRB03KT 5SM BR BKN025
FM202000 VRB03KT P6SM SCT250
```

The first line of the TAF is decoded as follows:

| Item      | Description                                                                                                 |
| --------- | ----------------------------------------------------------------------------------------------------------- |
| KHIO      | The station identifier (Hillsboro Airport)                                                                  |
| 192323Z   | The date and time of the report (19th day of the month at 23:23 UTC)                                        |
| 2000/2024 | The forecast period (from the 20th day of the month at 00:00 UTC to the 20th day of the month at 24:00 UTC) |
| 12011KT   | Wind from 120 degrees at 11 knots (in true heading)                                                         |
| P6SM      | Visibility of greater than 6 statute miles                                                                  |
| BKN060    | Broken clouds at 6000 feet AGL                                                                              |

The second line of the TAF is decoded as follows:

| Item    | Description                                                       |
| ------- | ----------------------------------------------------------------- |
| 200500  | The forecast period (from the 20th day of the month at 05:00 UTC) |
| 09004KT | Wind from 90 degrees at 4 knots (in true heading)                 |
| P6SM    | Visibility of greater than 6 statute miles                        |
| SCT025  | Scattered clouds at 2500 feet AGL                                 |

The third line of the TAF is decoded as follows:

| Item    | Description                                                       |
| ------- | ----------------------------------------------------------------- |
| 201400  | The forecast period (from the 20th day of the month at 14:00 UTC) |
| VRB03KT | Variable wind at 3 knots                                          |
| 5SM     | Visibility of 5 statute miles                                     |
| BR      | Mist (visibility reduced to less than 6 statute miles)            |
| BKN025  | Broken clouds at 2500 feet AGL                                    |

The fourth line of the TAF is decoded as follows:

| Item    | Description                                                       |
| ------- | ----------------------------------------------------------------- |
| 202000  | The forecast period (from the 20th day of the month at 20:00 UTC) |
| VRB03KT | Variable wind at 3 knots                                          |
| P6SM    | Visibility of greater than 6 statute miles                        |
| SCT250  | Scattered clouds at 25,000 feet AGL                               |

## METAR and TAF in practice

As an S1, the most common use for weather forecasts is to verify the altimeter before issuing a clearance, to ensure the aircraft's filed flight level is valid.

### Example 1

The METAR at KPDX is as follows. What is the wind and altimeter?

```plaintext
METAR KPDX 131753Z 08004KT 10SM FEW250 12/03 A3035 RMK AO2 SLP277 T01170033
```

{{% details title="Show answer" closed="true" %}}

The wind is 60° at 4 knots, 80° minus 20° correction for magnetic deviation. The altimeter is 30.35.

| Item      | Description                                                              |
| --------- | ------------------------------------------------------------------------ |
| KPDX      | The station identifier (Portland International Airport)                  |
| 131753Z   | The date and time of the report (13th day of the month at 17:53 UTC)     |
| 08004KT   | Wind from 80 degrees at 4 knots (in true heading)                        |
| 10SM      | Visibility of 10 statute miles                                           |
| FEW250    | Few clouds at 25,000 feet AGL                                            |
| 12/03     | Temperature of 12 degrees Celsius and dew point of 3 degrees Celsius     |
| A3035     | Altimeter setting of 30.35 inches of mercury                             |
| RMK AO2   | Remarks indicating the station is automated with precipitation sensor    |
| SLP277    | Sea-level pressure of 1027.7 hPa                                         |
| T01170033 | Temperature of 11.7 degrees Celsius and dew point of 3.3 degrees Celsius |

{{% /details %}}

### Example 2

The METAR at KSEA is as follows. What is the wind and altimeter?

```plaintext
METAR KSEA 131800Z VRB02KT 10SM FEW040 FEW150 FEW210 11/03 A3044
```

{{% details title="Show answer" closed="true" %}}

The wind is variable at 2 knots, which is considered **calm** since the wind speed is below 3 knots. The altimeter is 30.44.

| Item    | Description                                                          |
| ------- | -------------------------------------------------------------------- |
| KSEA    | The station identifier (Seattle-Tacoma International Airport)        |
| 131800Z | The date and time of the report (13th day of the month at 18:00 UTC) |
| VRB02KT | Variable wind at 2 knots (in true heading)                           |
| 10SM    | Visibility of 10 statute miles                                       |
| FEW040  | Few clouds at 4000 feet AGL                                          |
| FEW150  | Few clouds at 15,000 feet AGL                                        |
| FEW210  | Few clouds at 21,000 feet AGL                                        |
| 11/03   | Temperature of 11 degrees Celsius and dew point of 3 degrees Celsius |
| A3044   | Altimeter setting of 30.44 inches of mercury                         |

{{% /details %}}

### Example 3

The TAF at KSEA is as follows. What will the cloud cover be at KSEA at 21:00 UTC on the 13th?

```plaintext
TAF KSEA 131129Z 1312/1418 03006KT P6SM FEW250
FM132100 35010KT P6SM FEW250
FM141100 02008KT P6SM SCT250
```

{{% details title="Show answer" closed="true" %}}

At 21:00 UTC on the 13th, the cloud cover will be few clouds at 25,000 feet AGL.

First line:

| Item      | Description                                                                                                 |
| --------- | ----------------------------------------------------------------------------------------------------------- |
| KSEA      | The station identifier (Seattle-Tacoma International Airport)                                               |
| 131129Z   | The date and time of the report (13th day of the month at 11:29 UTC)                                        |
| 1312/1418 | The forecast period (from the 13th day of the month at 12:00 UTC to the 14th day of the month at 18:00 UTC) |
| 03006KT   | Wind from 30 degrees at 6 knots (in true heading)                                                           |
| P6SM      | Visibility of greater than 6 statute miles                                                                  |
| FEW250    | Few clouds at 25,000 feet AGL                                                                               |

Second line:

| Item    | Description                                                       |
| ------- | ----------------------------------------------------------------- |
| 132100  | The forecast period (from the 13th day of the month at 21:00 UTC) |
| 35010KT | Wind from 350 degrees at 10 knots (in true heading)               |
| P6SM    | Visibility of greater than 6 statute miles                        |
| FEW250  | Few clouds at 25,000 feet AGL                                     |

Third line:

| Item    | Description                                                       |
| ------- | ----------------------------------------------------------------- |
| 141100  | The forecast period (from the 14th day of the month at 11:00 UTC) |
| 02008KT | Wind from 20 degrees at 8 knots (in true heading)                 |
| P6SM    | Visibility of greater than 6 statute miles                        |
| SCT250  | Scattered clouds at 25,000 feet AGL                               |

{{% /details %}}
