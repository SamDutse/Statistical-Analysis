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
```python
import pandas as pd
import numpy as np
import scipy.stats as stats

# Load the dataset
df = pd.read_csv("synthetic_health_insurance_survey.csv")

# Mapping yearly premium ranges to midpoint values
premium_mapping = {
    "Less than ₦3,000": 2500,
    "₦3,000 – ₦5,000": 4000,
    "₦5,001 – ₦7,000": 6000,
    "₦7,001 – ₦10,000": 8500,
    "More than ₦10,000": 11000
}

df["Yearly Premium (NGN)"] = df["Yearly Premium Willing to Pay"].map(premium_mapping)

# Compute statistics
sample_mean = np.mean(df["Yearly Premium (NGN)"])
sample_std = np.std(df["Yearly Premium (NGN)"], ddof=1)
n = len(df["Yearly Premium (NGN)"])

# Compute 95% confidence interval
confidence_level = 0.95
lower_bound, upper_bound = stats.norm.interval(confidence_level, loc=sample_mean, scale=sample_std / np.sqrt(n))

# Display Results
print(f"Estimated Yearly Contribution Willing to Pay: {sample_mean:.2f} NGN")
print(f"95% Confidence Interval: [{lower_bound:.2f}, {upper_bound:.2f}] NGN")

# Decision Making
required_threshold = 5000
if lower_bound >= required_threshold:
    print("✅ The insurance scheme is likely financially viable.")
else:
    print("⚠️ The estimated contributions are too low. Consider alternative funding.")
```

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

## Repository Structure
```
├── data/
│   ├── synthetic_health_insurance_survey.csv
├── analysis/
│   ├── feasibility_study.ipynb
├── README.md
```

## How to Use This Repository
1. Clone the repository:  
   ```bash
   git clone https://github.com/yourusername/health-insurance-feasibility.git
   ```
2. Install dependencies:  
   ```bash
   pip install pandas numpy scipy
   ```
3. Run the analysis script in Jupyter Notebook or Python.

## License
This project is open-source and available under the [MIT License](LICENSE).
