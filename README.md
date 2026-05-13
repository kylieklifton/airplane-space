# Spirit Crammed 193 Seats Per Flight. Then It Collapsed.

A scrollytelling project about how airlines have added seats to planes over the past 35 years, using federal flight data from the Bureau of Transportation Statistics.

## The Story

Spirit Airlines shut down on May 2, 2026. The ultra low-cost carrier had filed for bankruptcy twice in under a year. It owed $8.1 billion.

Spirit was known for cramming passengers in. Federal data shows the average Spirit flight carried 193 seats in 2025. Only Frontier fit more: 209 seats per flight. Delta averaged 171. United, 177. American, 174.

This project visualizes that transformation using BTS data, 3D aircraft models, and scroll-controlled comparisons.

## Key Findings

- The Boeing 737 went from 122 seats per flight in 1990 to 164 in 2025, a 34% increase
- Spirit averaged 193 seats per flight in 2025, Frontier averaged 209
- Every major U.S. airline added seats over 35 years except JetBlue
- The 747 went from 326 seats per flight in 1990 to 37 in 2025 as most converted to cargo

## Data Source

Bureau of Transportation Statistics, U.S. Department of Transportation. T-100 Domestic Segment (All Carriers), 1990-2025.

Download from: https://www.transtats.bts.gov/

The website only allows downloading one year at a time. I downloaded 37 CSV files and merged them.

### How to Get the Data

1. Go to TranStats: https://www.transtats.bts.gov/
2. Navigate to Aviation > Air Carrier Statistics > T-100 Domestic Segment
3. Select a year and download
4. Repeat for each year (1990-2026)
5. Merge the CSVs, keeping the header from only the first file

For the aircraft type lookup table:
1. Go to TranStats Aviation Support Tables
2. Download the Aircraft Types table
3. Save as T_AIRCRAFT_TYPES.csv

## Analysis

The key metric is average seats per departure:

```
Average seats per flight = SEATS / DEPARTURES_PERFORMED
```

This captures how airlines configure their cabins. A higher number means more seats per flight, whether from larger aircraft variants or denser seating layouts.

The analysis notebook joins the T-100 data with the aircraft type lookup table, groups by airline or aircraft family, and calculates yearly averages.

## Features

- Full-bleed hero image with headline overlay
- Two 3D aircraft models via Sketchfab (1956 Super Constellation, Boeing 737 MAX)
- Scroll-controlled camera movement through 3D cabins
- Before/after image sliders controlled by scroll
- Datawrapper chart embeds

## How to Run

1. Open the project folder in VS Code
2. Right-click index.html and select "Open with Live Server"

## Tools Used

- Python/Pandas for data analysis
- Datawrapper for charts
- GSAP ScrollTrigger for scroll animations
- Sketchfab Viewer API for 3D models
- Claude Code to make custom image slider tools that worked with scrollama

## Author

Kylie Clifton
