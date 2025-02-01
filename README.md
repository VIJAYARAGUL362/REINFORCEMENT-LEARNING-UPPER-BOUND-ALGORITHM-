# Ad Click-Through Rate (CTR) Optimization with UCB

This project demonstrates the application of the Upper Confidence Bound (UCB) algorithm to optimize ad selection for maximizing click-through rate (CTR).  It simulates an online advertising campaign, leveraging a historical dataset of ad impressions and user clicks to learn and adapt ad-serving strategies.

## Table of Contents

*   [Introduction](#introduction)
*   [Dataset](#dataset)
*   [Algorithm](#algorithm)
*   [Requirements](#requirements)
*   [Usage](#usage)
*   [Output](#output)
*   [Implementation Details](#implementation-details)
*   [Discussion](#discussion)
*   [Contributing](#contributing)
*   [License](#license)

## Introduction

In online advertising, maximizing CTR is crucial for campaign success.  The multi-armed bandit problem provides a framework for addressing this challenge, where different ads represent "arms" with unknown click probabilities. The goal is to find the optimal balance between *exploration* (trying out different ads to learn their performance) and *exploitation* (choosing the ad currently believed to be the best).

The UCB algorithm is a popular solution to this problem. It calculates an "upper confidence bound" for each ad, representing a plausible upper limit on its true CTR.  By selecting the ad with the highest UCB, the algorithm intelligently explores promising options while still exploiting known good performers.

This project simulates an ad campaign using the UCB strategy.  It processes historical data, iteratively selects ads based on UCB, observes simulated user clicks, and updates its knowledge of ad performance.

## Dataset

The project utilizes a CSV file named `Ads_CTR_Optimisation.csv`.  This dataset contains historical records of ad impressions and user interactions.  Each row corresponds to a single ad impression and includes the following columns (likely, as the exact columns depend on your data):

*   `Ad ID`: A unique identifier for the ad shown.
*   `Click`: A binary indicator (0 or 1) representing whether the user clicked on the ad (1) or not (0).

This dataset serves as the basis for training and evaluating the UCB algorithm.

## Algorithm

The UCB algorithm works as follows:

1.  **Initialization:** For each ad, initialize the number of times it has been shown and the sum of rewards (clicks) received.

2.  **Iteration:** For each round of the simulation:
    *   Calculate the UCB for each ad using the formula:
        ```
        UCB = Average Reward + c * sqrt(ln(Total Impressions) / Number of Impressions)
        ```
        Where:
        *   `Average Reward` is the average click rate for the ad.
        *   `c` is a confidence parameter (typically a small positive constant).
        *   `Total Impressions` is the total number of ads shown across all rounds.
        *   `Number of Impressions` is the number of times the specific ad has been shown.

    *   Select the ad with the highest UCB.
    *   Observe the simulated user response (click or no click).
    *   Update the number of impressions and sum of rewards for the selected ad.

3.  **Repeat:** Continue iterating for a predefined number of rounds.

## Requirements

*   Python 3.x
*   NumPy: For numerical operations.
*   Pandas: For data handling and manipulation.
*   Matplotlib: For creating visualizations.

Install the required libraries using pip:

```bash
pip install numpy pandas matplotlib
