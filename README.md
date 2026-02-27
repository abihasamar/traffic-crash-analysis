# traffic-crash-analysis
"Analysis of 7.7M traffic crashes identifying severe crash patterns and building predictive model
# Severe Traffic Crash Analysis & Prediction

##  Project Overview
Analysis of 7.7 million US traffic crash records (2016-2023) to identify patterns in severe crashes and build a machine learning model for predicting high-risk conditions.

**Goal:** Understand what conditions lead to severe crashes and create a risk detection system for traffic safety applications.

## Key Findings
### 1. Severe crashes are rare but predictable
<img width="551" height="283" alt="Imbalanced" src="https://github.com/user-attachments/assets/b48c7734-29e9-43eb-8868-667fbb52624a" />

- Only **1.8%** of crashes are severe, but they follow clear patterns
  
### 2. Geographic concentration
<img width="1772" height="1132" alt="States" src="https://github.com/user-attachments/assets/6f42d626-bb3f-4ee1-997c-d5a68c8cd11a" />

- High-risk states (MD, AR, WY, WI, DE): **5-9%** severe crash rates
- Low-risk states (MN, ND, OK, RI, SC): **1-2%** severe crash rates
### 3. Infrastructure gap: "Invisible Junctions"
<img width="1287" height="1197" alt="Road Insfrastructure" src="https://github.com/user-attachments/assets/cf3490d3-8bf9-436f-a699-90bf7621cd5f" />

- Non-signaled junctions: **862 severe crashes**
- Signaled junctions: **15 severe crashes**
- **57x higher risk** at junctions without traffic signals
### 4. Temporal patterns
<img width="589" height="241" alt="Unsignaled Junction" src="https://github.com/user-attachments/assets/94f6c72d-72a5-4a3f-8e9e-1739ad9d4225" />

- Peak: **7:00 AM** (morning commute)
- Elevated throughout afternoon (1-6 PM)
- NOT dominated by nighttime hours
### 5. Weather paradox
<img width="554" height="225" alt="Weather" src="https://github.com/user-attachments/assets/194f055f-63d0-435c-8d93-2acf677248ab" />

- **33% elevated risk** in clear, fair weather
- Theory: Good conditions → higher speeds + reduced caution → more severe outcomes
##  Technical Approach
### Data Cleaning
- Removed **1.7M duplicate records**
- Dropped columns with >20% missing values
- Handled remaining missing data with minimal loss
- Recoded severity: Minor (1-2), Moderate (3), Severe (4)
### Feature Engineering
- **Temporal:** Hour of day, day of week, twilight indicators
- **Weather:** Temperature, humidity, precipitation, wind, visibility
- **Infrastructure:** Junction type, traffic signals, crossings, stop signs
- **Geographic:** State, coordinates, distance affected
### Modeling
- **Algorithm:** XGBoost Classifier
- **Why XGBoost:** Handles non-linear relationships between crash conditions and severity
- **Class Imbalance:** 1.8% severe crashes required careful threshold optimization
### Threshold Selection
- **Chosen threshold:** 0.20 (lower than default 0.50)
- **Reasoning:** In public safety, false positives (flagging safe conditions as risky) are acceptable; false negatives (missing actual high-risk conditions) are not
- **Result:** 95% recall, 3.78% precision

## Results
| Metric | Value |
|--------|-------|
| **Recall (Severe)** | 95.45% |
| **Precision (Severe)** | 3.78% |
| **Overall Accuracy** | 56.40% |
**Interpretation:** The model successfully identifies 95% of severe crash conditions, making it suitable as a risk flagging system where catching dangerous conditions is prioritized over precision.


## 🛠️ Tools & Technologies

- **Python 3.x**
- **Data Processing:** Pandas, NumPy
- **Modeling:** XGBoost, Scikit-learn
- **Visualization:** Matplotlib, Seaborn
- **Presentation:** PowerPoint, Data Storytelling

---

## Repository Structure
```
traffic-crash-analysis/
├── README.md                  
├── presentation/
│   └── Traffic Data Analysis.pptx          # Final presentation with visual storytelling
├── images/
│   ├── Imbalanced.png
│   ├── States.png
│   ├── Peak Hours.png
|   ├──Unsignaled Junction.png
|   ├──Road Infrastructure.png
|   └──Weather.png
└── notebooks/               
|   ├──Traffic Analysis_Feature Engineering_Model Training.ipynb
|   └──Traffic analysis_Data PreProcessing.ipynb
---

## Key Takeaways

1. **Data storytelling matters:** Translating technical findings into compelling narratives makes insights actionable
2. **Context drives decisions:** Model metrics must align with real-world costs (false negatives vs false positives)
3. **Surprising patterns exist:** Counterintuitive findings (clear weather risk) challenge assumptions and drive better policy

---




Dataset: US Traffic Crash Data (2016-2023)
Team: [Your team members' names if this was group work]
