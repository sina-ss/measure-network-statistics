# Measure Network Statistics

## Overview

This project is dedicated to reviewing Internet Service Providers (ISPs) across various provinces of the country. One of the key features of this platform is the ability to assess and display average download and upload speeds for ISPs, mapping them to a percentage scale where 100% represents ideal performance and 0% is very poor.

## Features

### 1. ISP Reviews

Users can:

- Submit reviews for different ISPs based on their experiences.
- Rate ISPs based on connectivity, customer service, and pricing.
- View average ratings and user comments for each ISP.

### 2. Speed Assessment

Using collected speed data, the platform provides a visual representation of:

- Average download and upload speeds.
- Speed performance percentage based on a logistic curve mapping.

The logistic curve provides a smooth transition between poor and ideal speeds, making the representation intuitive and user-friendly.

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

### 4. Interactive Graphs

Users can interact with visual representations, such as graphs and plots, to understand the performance of ISPs better. This includes:

- Comparisons of average speeds among different ISPs.
- Speed trend over time.

## Usage

1. **ISP Review**: Navigate to the 'Reviews' section to submit or read reviews for different ISPs.
2. **Speed Assessment**: Visit the 'Speed Assessment' section to view the average speeds and corresponding percentages for ISPs.

## Technical Details

The logistic function used for speed-to-percentage mapping is defined as:

\[
P(s) = \frac{L}{{1 + e^{-k(s - s_0)}}}
\]

Where:

- \( P(s) \) is the percentage for a given speed \( s \).
- \( L \) is the maximum value of the curve (typically 100 for percentages).
- \( k \) determines the steepness of the curve.
- \( s_0 \) is the speed value where \( P(s) \) is half of \( L \).

The parameters \( L \), \( k \), and \( s_0 \) were determined using a machine learning approach to fit the curve to hypothetical data, representing our understanding of "poor", "average", and "ideal" speeds.

Feel free to adjust the content as necessary to better fit your project's specifics.
