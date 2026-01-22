# Advance Mathematics Assignment

## 1. Methodology

The overall workflow followed in this project is illustrated below:

**Data Collection → Data Pre-processing → Feature Transformation → PDF Parameter Learning → Result Analysis & Visualization**

* **Data Collection**: India Air Quality Dataset (Kaggle)
* **Data Pre-processing**: Handling missing values, selecting the NO₂ feature
* **Feature Transformation**: Roll-number-based nonlinear transformation
* **Parameter Learning**: Maximum Likelihood Estimation (MLE)
* **Result Analysis**: Visualization of empirical PDF and learned PDF

---

## 2. Description

* **Dataset**: India Air Quality Data (Kaggle)

* **Feature Used**: NO₂ concentration

* **Transformation Applied**:
  [
  z = x + a_r \sin(b_r x)
  ]
  where:

  * (a_r = 0.05 \times (r \bmod 7))
  * (b_r = 0.3 \times ((r \bmod 5) + 1))
  * (r) is the university roll number

* **PDF Assumed**:
  [
  \hat{p}(z) = c,e^{-\lambda (z-\mu)^2}
  ]

* **Learning Method**: Maximum Likelihood Estimation (closed-form solution)

* **Learned Parameters**:

  * (\mu): Mean of transformed data
  * (\lambda): Inverse variance parameter
  * (c): Normalization constant

---

## 3. Input / Output

### Input

* CSV file containing air quality measurements
* Feature: NO₂ values

### Output

* Learned parameters (\mu), (\lambda), and (c)
* Empirical PDF (histogram of transformed data)
* Best-fit learned PDF curve

Example output table:

| Sample | Actual Distribution | Learned Distribution | Result |
| ------ | ------------------- | -------------------- | ------ |
| z₁     | High Density        | High Density         | ✓      |
| z₂     | Medium Density      | Medium Density       | ✓      |
| z₃     | Low Density         | Medium Density       | ✗      |

---

## 4. Visualization

* **Histogram**: Represents the empirical probability density of the transformed variable (z)
* **Smooth Curve**: Represents the learned Gaussian PDF using MLE

The learned curve fits the central tendency of the data well. Deviations at extreme tails are expected due to skewness and outliers in real-world NO₂ measurements.

![PDF Learning Result](/assets/graph.png)

---

## 5. Algorithm Used

**Maximum Likelihood Estimation (MLE)**

* Parameters are learned by maximizing the likelihood of the transformed data
* For Gaussian PDFs, MLE admits a closed-form solution
* This ensures deterministic, optimal, and reproducible parameter learning

---

## 6. Files Included

* `Advance_Mathematics.ipynb` – Main Jupyter Notebook containing code and analysis
* `data.csv` – Air quality dataset (uploaded separately)
* `README.md` – Project documentation

---

## 7. How to Run

1. Upload `data.csv` to the working directory
2. Open `Advance_Mathematics.ipynb`
3. Run all cells sequentially
4. Observe learned parameters and PDF visualization

---

## 8. Conclusion

This project demonstrates how probability density functions can be learned from real-world data using statistical learning techniques. The use of roll-number-based nonlinear transformation ensures personalization, while Maximum Likelihood Estimation provides an exact and reliable method for parameter learning.

