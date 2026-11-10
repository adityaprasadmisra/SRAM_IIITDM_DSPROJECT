# SRAM Stability and Failure Probability Analysis

**An AI/ML-based investigation of SRAM reliability, fault classification, and Static Noise Margin prediction under Process, Voltage, and Temperature (PVT) variations.**

## 1. Understanding SRAM

### What is SRAM?

Static Random Access Memory (SRAM) is a type of volatile semiconductor memory used to store digital information. It is widely used in processor caches, registers, embedded systems, and high-speed memory architectures.

Unlike DRAM, SRAM does not require periodic refreshing to retain stored information as long as power is supplied.

SRAM stores information using bistable circuits constructed using transistors. A commonly used implementation is the **6-Transistor (6T) SRAM cell**.

### Architecture of a 6T SRAM Cell

A conventional 6T SRAM cell consists of:

- **4 transistors forming two cross-coupled inverters:** These create a bistable storage element that holds one bit of information.
- **2 access transistors:** These connect the storage nodes to the bit lines during read and write operations.

The six transistors are connected to:
- Word Line (WL)
- Bit Line (BL)
- Complementary Bit Line (BLB)
- Storage nodes Q and QB
- Supply voltage (VDD)
- Ground (GND)

https://github.com/user-attachments/assets/75e78a76-33e4-4f05-bc1a-3f5d3e5b9cd5

The cross-coupled inverters maintain complementary logic states at Q and QB.

### How Does an SRAM Cell Work?

**1. Hold Operation**

When the Word Line is LOW, the access transistors are OFF. The cross-coupled inverters maintain the previously stored bit.

**2. Read Operation**

The bit lines are precharged, typically to VDD. When the Word Line becomes HIGH, the access transistors connect the storage nodes to the bit lines. A small voltage difference develops between BL and BLB, which is detected by a sense amplifier.

**3. Write Operation**

The desired data and its complement are driven onto BL and BLB. Activating the Word Line connects the bit lines to the internal storage nodes, allowing the new value to overwrite the previous state.

### Static Noise Margin (SNM)

Static Noise Margin is an important measure of SRAM cell stability. It represents the maximum DC noise voltage that a cell can tolerate without changing its stored state.

A higher SNM generally indicates better resistance to disturbances.

Two important measurements are:

- **Hold SNM:** Stability when the cell is not performing a read or write operation.
- **Read SNM:** Stability during a read operation, when the access transistors connect the storage nodes to the bit lines.

The butterfly curve, obtained by plotting the voltage transfer characteristics of the two cross-coupled inverters, is commonly used to visualize and estimate SNM.

### What Affects SRAM Stability?

SRAM stability can be affected by:

- Process variations in transistor characteristics.
- Supply voltage fluctuations.
- Temperature variations.
- Transistor threshold-voltage (Vth) drift.
- Resistive opens and bridging defects.
- Read and write disturbances.

These effects can change transistor currents, internal node voltages, access behavior, and ultimately the stability of the stored data.

---

## 2. SRAM Architecture and Working – Video Explanation

Watch the video walkthrough to understand the 6T SRAM architecture, individual MOSFET roles, storage mechanism, and read/write operations.

**Video walkthrough:**

<!-- Upload your video through GitHub's README editor and replace this comment with its generated video URL. -->

---

## 3. Project Overview

This project investigates SRAM stability and failure behavior using statistical analysis and machine learning.

The objective is to understand how electrical characteristics and fault mechanisms influence SRAM stability, and to develop predictive models for SNM estimation and fault classification.

### Project Objectives

- Analyze SRAM electrical characteristics across PVT corners.
- Investigate the impact of different fault mechanisms.
- Perform data cleaning and exploratory data analysis.
- Conduct statistical testing and feature engineering.
- Develop regression models for SNM prediction.
- Build machine learning models for fault classification.
- Evaluate model generalization across PVT corners.
- Apply SHAP-based explainability to understand model behavior.

## 4. Fault Categories

| Class | Fault Type |
|---|---|
| 0 | Healthy |
| 1 | Resistive Open |
| 2 | Bridging |
| 3 | Storage Vth Drift |
| 4 | Access Vth Drift |

## 5. Dataset

The dataset contains 450 samples, 33 features, and 15 PVT corners.

Important electrical parameters include:

- Supply voltage (`vdd_v`)
- Temperature (`temperature_c`)
- Drain current (`i_ddq_uA`)
- Write delay (`t_write_ps`)
- Write peak current (`i_write_peak_mA`)
- Bit-line voltage difference (`dv_bl_strobe_mV`)
- Hold SNM (`snm_hold_v`)
- Read SNM (`snm_read_v`)

## 6. Project Workflow

1. Data Understanding
2. Data Cleaning
3. Exploratory Data Analysis
4. Statistical Analysis
5. Feature Engineering
6. SNM Regression
7. SRAM Fault Classification
8. Model Explainability

## 7. Technologies Used

- Python
- Pandas and NumPy
- Matplotlib and Seaborn
- SciPy and Scikit-posthocs
- Scikit-learn
- XGBoost
- SHAP
- Jupyter Notebook

## 8. Machine Learning Results

### Fault Classification

| Model | Accuracy | Macro F1 |
|---|---:|---:|
| Random Forest | 82.22% | 0.6828 |
| Regularized Random Forest | 81.33% | 0.7112 |
| XGBoost | 80.67% | 0.6848 |

### SNM Regression

| Target | Model | MAE | RMSE | R² |
|---|---|---:|---:|---:|
| Hold SNM | Linear Regression | 0.03081 | 0.04630 | 0.92662 |
| Hold SNM | Random Forest | 0.03114 | 0.04256 | 0.93720 |
| Read SNM | Linear Regression | 0.06076 | 0.08153 | 0.47977 |
| Read SNM | Random Forest | 0.06899 | 0.10535 | 0.15072 |

*These results come from different evaluation experiments and should not be interpreted as directly comparable validation results.*

## 9. Repository Structure

```text
SRAM_IIITDM_DSPROJECT/
│
├── data/
├── notebooks/
├── models/
├── reports/
├── src/
├── README.md
└── requirements.txt
```

## 10. Installation

Clone the repository:

```bash
git clone https://github.com/adityaprasadmisra/SRAM_IIITDM_DSPROJECT.git
cd SRAM_IIITDM_DSPROJECT
```

Create a virtual environment:

```bash
python -m venv venv
```

Activate it on Windows:

```powershell
venv\Scripts\activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Launch Jupyter:

```bash
jupyter notebook
```

Run the notebooks in numerical order.

## 11. Limitations and Future Work

- Expand the dataset across more PVT corners.
- Improve simulation convergence and data reliability.
- Investigate robust cross-corner generalization.
- Explore calibrated failure-probability estimation.
- Integrate predictions into an interactive SRAM analysis dashboard.
- Validate results using additional circuit simulations and experimental measurements.

The current results are based on the available simulation dataset and do not establish performance on fabricated SRAM hardware.

## Authors

**IIITDM Kancheepuram**

Academic project on SRAM stability, fault analysis, and machine learning.

---

**SRAM Reliability | 6T SRAM | Static Noise Margin | PVT Variation | Fault Classification | Machine Learning**
