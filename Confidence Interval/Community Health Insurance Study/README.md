# Feasibility Study for a Mini Health Insurance Scheme in a Local Community

## Project Overview
The goal of this project is to assess the feasibility of a mini health insurance scheme in local communities of Plateau State, Nigeria. The study aims to:

- Improve access to primary healthcare at an affordable rate.
- Reduce self-medication, which can lead to complications.
- Ensure the sustainability of primary healthcare centers through community contributions.

## Problem Statement
Many residents rely on out-of-pocket payments for healthcare, leading to financial hardship and increased cases of self-medication. A sustainable community health insurance scheme can provide affordable and reliable healthcare access. The project seeks to determine the financial viability of such a scheme using survey data.

## Data Collection
A survey was conducted among residents to collect information on:

- Common health challenges they visit primary healthcare centers for.
- Willingness to pay for healthcare under different pricing models.
- Preferred insurance pricing plans (e.g., fixed yearly payments vs. co-payment per visit).

## Methodology
The feasibility of the insurance scheme is evaluated by estimating the **95% confidence interval** of the mean amount residents are willing to pay. The decision rule is:

- If the lower bound of the confidence interval exceeds the required sustainability threshold, the scheme is viable.
- Otherwise, adjustments may be needed (e.g., government subsidies, community sensitization, alternative pricing models).

## Statistical Analysis
We use Python to:

1. **Load the survey data** (synthetic dataset with 1,000 responses).
2. **Map categorical responses to numeric values**.
3. **Calculate the mean, standard deviation, and sample size**.
4. **Compute the 95% confidence interval** using `scipy.stats.norm.interval`.
5. **Compare the confidence interval with the sustainability threshold**.

## Implementation
### Dataset
The dataset contains:

- **Age Group**
- **Employment Status**
- **Health Challenges**
- **Yearly Premium Willing to Pay**

### Python Code
view code in notebook above

## Results & Interpretation
- The **mean yearly premium residents are willing to pay** is calculated.
- The **95% confidence interval** provides a range within which the true mean likely falls.
- If the lower bound is above the threshold, the scheme is financially sustainable.

## Recommendations
If the scheme is **not viable**, possible solutions include:
- Adjusting the contribution model (e.g., reducing the 10% co-payment).
- Seeking government subsidies or NGO partnerships.
- Increasing awareness to encourage more participation.

## Conclusion
Confidence intervals help in making **data-driven policy decisions** regarding community health financing. This approach ensures that insurance schemes are both affordable and financially sustainable for long-term impact.


## License
This project is open-source and available under the [Bluehouse Technologies Ltd License](LICENSE).
