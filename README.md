[README.md](https://github.com/user-attachments/files/23059411/README.md)
#  NOAA Lightning Strikes Data Analysis

![Python](https://img.shields.io/badge/Python-3.9%2B-blue?logo=python)
![Pandas](https://img.shields.io/badge/Pandas-Data_Analysis-yellow?logo=pandas)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-orange?logo=plotly)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Active-brightgreen)

---

##  Overview
This project explores **NOAA (National Oceanic and Atmospheric Administration)** lightning strike data to uncover seasonal and monthly patterns in strike frequency.  
The goal is to **clean, transform, and visualize** the dataset to identify when and where lightning activity is most intense.

---

##  Objectives
-  Load and clean real-world CSV data  
-  Convert date columns into datetime format  
-  Group and aggregate lightning strikes by month  
-  Visualize results to show clear trends and insights  

---

##  Technologies Used

| Library | Purpose |
|----------|----------|
| **Pandas** | Data manipulation and aggregation |
| **Matplotlib** | Data visualization |
| **Datetime** | Handling timestamps and date conversions |
| **NumPy** *(optional)* | Numerical operations |

---

##  Project Structure

```
 NOAA-Lightning-Strikes-Analysis
 ┣ 📄 Data Analysis Project NOAA Strikes.ipynb     # Jupyter Notebook
 ┣ 📄 lightening strikes dataset.csv               # Dataset
 ┣ 📄 README.md                                   # Project documentation
 ┗ 📄 LICENSE                                     # MIT License (optional)
```

---

##  Getting Started

### 1️ Clone the Repository
```bash
git clone https://github.com/<your-username>/NOAA-Lightning-Strikes-Analysis.git
cd NOAA-Lightning-Strikes-Analysis
```

### 2️ Install Dependencies
Make sure you have Python 3.8+ installed, then run:
```bash
pip install pandas matplotlib
```

### 3️ Open the Notebook
You can use **PyCharm**, **JupyterLab**, or **VS Code** to open:
```
Data Analysis Project NOAA Strikes.ipynb
```

---

##  Analysis Workflow

This section outlines the key steps performed in the lightning strikes analysis process,  from loading the data to visualizing the final insights.

---

###  Step 1,  Import Required Libraries
```python
import pandas as pd
import matplotlib.pyplot as plt
import datetime as dt
```

---

###  Step 2 ,  Load the Dataset
```python
df = pd.read_csv("lightening strikes dataset.csv")
df.head()
```

---

###  Step 3 ,  Convert Dates and Extract Month Information
```python
df['date'] = pd.to_datetime(df['date'])
df['month'] = df['date'].dt.month
df['month_txt'] = df['date'].dt.month_name().str.slice(stop=3)
```

---

###  Step 4 ,  Group and Aggregate Data
```python
df_by_month = (
    df.groupby(['month', 'month_txt'])
      .sum(numeric_only=True)
      .sort_values('month')
      .reset_index()
)
```

---

###  Step 5 ,  Visualize Monthly Lightning Strikes
```python
plt.bar(
    x=df_by_month['month_txt'],
    height=df_by_month['number_of_strikes'],
    label="Number of Strikes"
)
plt.xlabel("Months (2018)")
plt.ylabel("Number of Lightning Strikes")
plt.title("Number of Lightning Strikes in 2018 by Month")
plt.legend()
plt.show()
```

---

###  Step 6 ,  Interpret Results
The resulting bar chart highlights which months experienced the highest lightning activity, revealing clear seasonal patterns.

Example chart placeholder:
```
![Lightning Chart](images/plot.png)
```

---

##  Insights & Learnings
-  Learned how to handle and analyze time-series data in pandas  
-  Observed clear seasonal trends in lightning activity  
-  Created polished visualizations using Matplotlib  
-  Reinforced workflow for real-world data projects (read → clean → analyze → visualize)

---

##  Future Improvements
- Integrate **severe weather data** (temperature, rainfall, etc.) for correlation analysis  
- Add **geographic visualizations** with libraries like `geopandas` or `plotly`  
- Automate analysis for multiple years of NOAA datasets  

---

##  License
This project is licensed under the **MIT License**.  
See the [LICENSE](LICENSE) file for more details.

---

##  Contributing
Pull requests are welcome!  
If you have ideas for better visualizations or data sources, feel free to open an issue or submit a PR.

---

##  Author
**Bertram Allen**  
📧 [b.d.allen512@gmail.com]  
💼 [https://www.linkedin.com/in/darrius-allen-247472b4/]

> “Data reveals the rhythms of nature,  even in lightning.”
