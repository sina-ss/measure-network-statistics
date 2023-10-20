# Measure Network Statistics

## Overview

This project is dedicated to reviewing Internet Service Providers (ISPs) across various provinces of the country. One of the key features of this platform is the ability to assess and display average download, upload speeds, ping measurements, and packet loss percentages for ISPs. These metrics are mapped to a percentage scale where 100% represents ideal performance and 0% indicates very poor performance.

## Features

### 1. ISP Reviews

Users can:

- Submit reviews for different ISPs based on their experiences.
- Rate ISPs based on connectivity, customer service, and pricing.
- View average ratings and user comments for each ISP.

### 2. Speed, Ping, and Packet Loss Assessment

Utilizing collected data, the platform offers a visual representation of:

- Average download and upload speeds.
- Speed performance percentage based on a logistic curve mapping.
- Ping performance percentage using an exponential decay function.
- Packet loss performance percentage using an exponential decay function.

These functions ensure a smooth transition between poor and ideal performance levels, enhancing the user's intuitive understanding.

### 3. Speed-to-Percentage Mapping

The conversion of speeds to percentages uses a sigmoid (logistic) curve. This curve ensures:

- Speeds below a set threshold are deemed subpar, leaning closer to 0%.
- As speeds near the "ideal" value, their corresponding percentage gravitates towards 100%.

For download speeds:

- Threshold speed: 13 Mbps (approximated to around 60%)
- Ideal speed: 40 Mbps (approximated to 100%)

For upload speeds:

- Threshold speed: 4 Mbps (approximated to around 60%)
- Ideal speed: 12 Mbps (approximated to around 100%)

### 4. Ping-to-Percentage Mapping

The conversion of ping values to percentages uses an exponential decay function, which assigns:

- Higher percentages to lower ping values.
- Rapidly decreasing percentages as ping values grow, emphasizing quality deterioration.

For ping measurements:

- Pings below 10 ms are close to 100%.
- Threshold ping of 40 ms is approximated to around 60%.
- Pings exceeding 200 ms approach 0%.

### 5. Packet Loss-to-Percentage Mapping

The relationship between packet loss percentages and their corresponding quality percentages is determined using an exponential decay function:

- Packet loss of 1% or less is ideal and corresponds to about 100% quality.
- Packet loss percentages around 5% are considered bad, indicating reduced quality.
- Packet loss percentages above 10% are deemed unusable, nearing 0% quality.

### Technical Details

The logistic function applied for speed-to-percentage conversion is:

$P(s) = \frac{L}{{1 + e^{-k(s - s_0)}}}$

Both the ping-to-percentage and packet loss-to-percentage mappings employ the exponential decay function:
$P(p) = L \times e^{-k \times p}$

Where:

- \( P(s) \) or \( P(p) \) represents the quality percentage for a given speed \( s \), ping \( p \), or packet loss \( p \).
- \( L \) stands for the curve's maximum value (typically 100 for percentages).
- \( k \) determines the curve's steepness or rate of decay.
- \( s_0 \) (only relevant for the logistic function) signifies the speed value where \( P(s) \) is half of \( L \).

The machine learning approach was utilized to determine the parameters \( L \), \( k \), and \( s_0 \), ensuring a fitting curve to hypothetical data that represents our understanding of "poor", "average", and "ideal" performance levels.

---

This updated `README.md` provides a comprehensive overview of your project. Adjust as needed to align with your platform's specifics.
