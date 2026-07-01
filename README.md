# CPGRAMS Grievance Intelligence 🏛️

A premium Streamlit dashboard for analysing 175,000+ public grievance records from the Government of India's Centralised Public Grievance Redress and Monitoring System (CPGRAMS).

## 🌟 Key Features

*   **Premium GUI:** Custom "dark glassmorphism" CSS theme offering a sleek, modern, and highly readable experience. Responsive layout utilizing the full width of modern displays.
*   **Animated KPI Metrics:** Live calculation of Total Grievances, Resolved percentage, Pending count, Median Resolution time, and geographical reach.
*   **Interactive Visualizations:** Powered by Plotly, featuring zooming, panning, and rich tooltips across various chart types (bar, line, pie, histogram, heatmap).
*   **Dynamic Filtering:** Universal sidebar filters allowing instant cross-filtering by Date Range, State / UT, Organisation, Gender, and Resolution Status. All charts instantly update based on active filters.
*   **Rich Analytics:** Deep-dives into monthly grievance trends, category breakdowns (Top 15 categories, Organisation → Category sunburst), resolution speed metrics by state and category, and demographic distribution.
*   **Data Explorer:** Built-in searchable datatable for interrogating the raw complaint subjects and filtering by specific keywords.
*   **Robust Data Pipeline:** Efficient loading, cleaning, date parsing, and mapping of real `.json` and `.xlsx` archives (~175K real 2023 records).

## 📁 Repository Structure

```
.
├── archive/
│   ├── no_pii_action_history.json   # Base action history records
│   ├── no_pii_grievance.json        # 175K+ real citizen complaints (2023)
│   └── CategoryCode_Mapping.xlsx    # Mappings for grievance categories
├── grievances.py                    # Data loading, cleaning, and transformation module 
├── analyze_grievances.py            # Static analysis pipeline outputting static PNG charts
├── dashboard.py                     # The interactive Streamlit dashboard application
└── README.md
```

## 🚀 How to Run the Dashboard

**1. Set up a virtual environment (Recommended)**
```bash
python3 -m venv venv
source venv/bin/activate
```

**2. Install dependencies**
Ensure you have the required packages installed in your environment:
```bash
pip install streamlit pandas numpy plotly openpyxl matplotlib seaborn wordcloud
```

*(Note: While `matplotlib`, `seaborn`, and `wordcloud` are used by the static analysis script `analyze_grievances.py`, the core dashboard relies primarily on `streamlit`, `pandas`, `numpy`, and `plotly`.)*

**3. Launch the Application**
```bash
streamlit run dashboard.py
```

The application will start, and a local web server will be hosted, typically at `http://localhost:8501`.

## 📊 The 6 Analytical Tabs
1.  **Overview**: Topline metrics, monthly trends, resolution percentage, and top 15 states by volume.
2.  **Resolution Analytics**: Detailed histograms of resolution timeframes, mean/median/percentile indicators, and a state-by-state average resolution speed comparison.
3.  **Category Insights**: Visualizing the most frequent types of complaints, their originating organizations, and identifying the slowest categories to resolve.
4.  **Demographics & Geography**: Gender splits, district-level hotspots, and a comprehensive State × Month grievance heatmap.
5.  **Organisation Performance**: Leaderboards highlighting the agencies receiving the most complaints and a deeply detailed performance table (Volume, Resolved, Median Days, Success %).
6.  **Data Explorer**: Full access to the raw data table with powerful keyword search functionality across complaint text.
