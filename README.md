# Measure Network Statistics

## Overview

This project is dedicated to reviewing Internet Service Providers (ISPs) across various provinces of the country. One of the key features of this platform is the ability to assess and display average download, upload speeds, and ping measurements for ISPs, mapping them to a percentage scale where 100% represents ideal performance and 0% is very poor.

## Features

### 1. ISP Reviews

Users can:

- Submit reviews for different ISPs based on their experiences.
- Rate ISPs based on connectivity, customer service, and pricing.
- View average ratings and user comments for each ISP.

### 2. Speed and Ping Assessment

Using collected speed data and ping measurements, the platform provides a visual representation of:

- Average download and upload speeds.
- Speed performance percentage based on a logistic curve mapping.
- Ping performance percentage based on an exponential decay function.

Both functions provide a smooth transition between poor and ideal performance levels, making the representation intuitive and user-friendly.

### 3. Speed-to-Percentage Mapping

The mapping from speeds to percentages is achieved using a sigmoid (logistic) curve. This curve ensures that:

- Speeds below the threshold are considered subpar and are closer to 0%.
- As speeds approach the "ideal" value, the percentage gets closer to 100%.

For download speeds:

- Threshold speed: 13 Mbps (mapped to around 60%)
- Ideal speed: 40 Mbps (mapped to 100%)

For upload speeds:

- Threshold speed: 4 Mbps (mapped to around 60%)
- Ideal speed: 12 Mbps (mapped to around 100%)

### 4. Ping-to-Percentage Mapping

The mapping from ping values to percentages is achieved using an exponential decay function. This function assigns high percentages to low ping values and decreases more rapidly as the ping increases, highlighting the degradation in quality.

For ping measurements:

- Ping below 10 ms: close to 100%
- Threshold ping: 40 ms (mapped to around 60%)
- Pings above 200 ms: close to 0%

### 5. Interactive Graphs

Users can interact with visual representations, such as graphs and plots, to understand the performance of ISPs better. This includes:

- Comparisons of average speeds and pings among different ISPs.
- Speed and ping trends over time.

## Usage

1. **ISP Review**: Navigate to the 'Reviews' section to submit or read reviews for different ISPs.
2. **Speed Assessment**: Visit the 'Speed Assessment' section to view the average speeds, pings, and corresponding percentages for ISPs.

## Technical Details

The logistic function used for speed-to-percentage mapping is defined as:

\[
P(s) = \frac{L}{{1 + e^{-k(s - s_0)}}}
\]

The exponential decay function used for ping-to-percentage mapping is:

\[
P(p) = L \times e^{-k \times p}
\]

Where:

- \( P(s) \) or \( P(p) \) is the percentage for a given speed \( s \) or ping \( p \).
- \( L \) is the maximum value of the curve (typically 100 for percentages).
- \( k \) determines the steepness of the curve or the rate of decay.
- \( s_0 \) is the speed value where \( P(s) \) is half of \( L \) (only relevant for the logistic function).

The parameters \( L \), \( k \), and \( s_0 \) were determined using a machine learning approach to fit the curve to hypothetical data, representing our understanding of "poor", "average", and "ideal" performance levels.

You can use this updated `README.md` for your project. Adjustments can be made as needed to better match the specifics of your platform.
