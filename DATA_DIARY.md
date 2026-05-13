# Data Diary

## Project Goal

Show how airlines have added seats to planes over time using federal flight data.

---

## Finding the Data

I started by looking for federal datasets with seat pitch or seat width measurements. I could not find any. No comprehensive U.S. government dataset tracks those variables across decades. Most seat-dimension information exists in airline seating charts or commercial databases, not in standardized public data.

I shifted the analysis toward cabin densification: how many seats airlines put on planes over time. The Bureau of Transportation Statistics (BTS) T-100 Domestic Segment dataset was the best option. It is an official federal aviation dataset spanning 1990 to 2025 and includes structured variables like available seats, departures performed, airline name, aircraft type, and year.

I downloaded the data from TranStats: https://www.transtats.bts.gov/

The website only allows downloading one year at a time. I downloaded 37 CSV files (1990-2026) and merged them into one file.

---

## Columns Selected

The T-100 dataset has dozens of columns. I only needed five: Seats (total available passenger seats on each flight segment), DepPerformed (departures actually flown, not scheduled), UniqueCarrierName (the airline), AircraftType (a numeric code identifying the plane model), and Year.

The AircraftType column contains codes, not names. A Boeing 737-800 shows up as code 628. To translate these, I downloaded the BTS Aircraft Types lookup table from the TranStats Aviation Support Tables. This let me match codes to manufacturer and model names.

---

## Key Metric

Average seats per departure = Seats / Departures Performed

This metric shows how airlines configured their cabins. A rising average means more seats per flight.

---

## Methodological Choices

**Rounding:** All seat counts in the article are rounded to whole numbers. The notebook keeps decimals for verification.

**Boeing family grouping:** I grouped Boeing aircraft by family (737, 747, 757, etc.) based on model names in the lookup table. All variants of the 737 (737-300, 737-800, MAX) are grouped together.

**Minimum threshold:** Only included aircraft or airlines with significant flight activity to avoid statistical noise from rare aircraft types.

**Time range:** 1990-2025. Earlier data is not available in the T-100 dataset.

---

## What the Data Does Not Show

The data counts seats. It does not measure seat pitch, seat width, or legroom. The increase in average seats is consistent with industry reports of tighter configurations, but the federal data confirms only the count.

---

## 3D Model Selection

I used two 3D models from Sketchfab to show the visual contrast between historic and modern cabins:

**1956 Lockheed Super Constellation:** This model was available on Sketchfab with interior annotations. The Super Constellation was a popular propeller aircraft of the 1950s, the same era as the Boeing 707. It represents what flying looked like before the jet age.

**Boeing 737 MAX:** This model shows a modern narrow-body cabin. The 737 is the focus of my quantitative analysis, so using it for the 3D comparison connects the visual story to the data.

I focused on Boeing aircraft because the 737 dominates U.S. domestic aviation and has the longest continuous presence in the data.

---

## Files

The merged T-100 data lives in data/t100_segment_1990_2026.csv. The aircraft type lookup table is data/T_AIRCRAFT_TYPES.csv. The two chart exports are data/chart1_boeing_slope.csv (Boeing 737 seat counts over time) and data/chart2_airlines_by_year.csv (airline comparisons from 1990 to 2025). The original 37 yearly downloads are in Data 1990-2026/. The analysis notebook is notebooks/analysis.ipynb.

---

## Sources

- Bureau of Transportation Statistics, U.S. Department of Transportation
- T-100 Domestic Segment (All Carriers), Air Carrier Statistics (Form 41 Traffic), 1990-2025
- BTS Aircraft Types lookup table from TranStats Aviation Support Tables
- 3D models via Sketchfab (CC Attribution)
