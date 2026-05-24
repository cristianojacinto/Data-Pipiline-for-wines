# 🍷 Data Pipeline for Wine Analysis

## Overview

This project demonstrates the implementation of a **robust and scalable data pipeline** for ingestion, transformation, and orchestration of wine data using **Apache Hop**, an open-source data engineering, integration, and orchestration platform maintained by the Apache Software Foundation.

The pipeline processes wine data from different countries, applying sophisticated transformations and generating aggregated and ordered reports for specialized analysis.

---

## 🎯 Project Objective

Automate the ingestion of wine data in CSV format and execute a series of complex transformations that segment data by country, apply specific filters, and generate processed files ready for analysis.

---

## 📊 Pipeline Architecture

### Processing Flow

```
Input CSV → Data Transformation → Filtering → Segmented Orchestration
```

The pipeline is divided into two main sub-pipelines that process data from **Italy (IT)** and **France (FR)** in distinct ways:

### **1️⃣ Ingestion Stage**
- **Input CSV**: Importation of wine data in CSV format

### **2️⃣ Transformation and Processing Stage**
- **Data Treatment**: Normalization of country codes
  - `France` → `FR`
  - `Italy` → `IT`

### **3️⃣ Filtering Stage**
- **Filter Rows**: Removes records that do not meet country criteria (IT or FR)
- Invalid data is automatically discarded

### **4️⃣ Orchestration Stage (Segmented)**

#### **Flow for Italy (IT)** ✅
- Italian data is exported directly to a formatted `.txt` file
- Output: `wine_data_output_IT.txt`

#### **Flow for France (FR)** 🇫🇷
1. **Field Selection**: Extraction of relevant fields
   - `country` (Country)
   - `province` (Province)
   - `price` (Price)
   - `points` (Points)

2. **First Sorting**: Initial sorting by price and points (ascending order)

3. **Aggregation by Location**: Grouping by country and province with calculations:
   - Sum of prices
   - Sum of points

4. **Second Sorting**: Final reordering of aggregated data by price and points

5. **Export**: Generation of processed file ready for analysis
   - Output: `france_aggregated_and_sorted.txt`

---

## 📁 File Structure

```
Data-Pipeline-for-wines/
└── outputs/             # Output files
    └── wine_data_output_IT.txt   # Raw Italian wine data
    └── france_aggregated_and_sorted.txt  # French data aggregated by region and sorted
├── README.md                    # Project documentation
├── pipeline.png                 # Pipeline architecture visualization
├── wine_world.csv               # Data source
└── pipeline_config/             # Apache Hop Configuration
    └── wine_data_pipeline.hpl   # Pipeline definition
```

---

## 🚀 Technologies Used

- **Apache Hop**: Open-source data orchestration platform
- **CSV**: Data input format
- **TXT**: Processed output format

---

## 💡 Key Features

✔️ Automated data ingestion  
✔️ Country code normalization  
✔️ Intelligent record filtering  
✔️ Country-specific processing  
✔️ Data aggregation and analysis  
✔️ Formatted report generation  
✔️ Scalable and maintainable orchestration  

---

## 📈 Use Cases

- **Comparative Analysis**: Compare characteristics of Italian and French wines
- **Aggregated Reports**: Generate summaries of prices and ratings by region
- **Data Warehousing**: Feed BI systems with processed data
- **ETL Automation**: Execute repetitive transformations without manual intervention

---

## 🔧 How to Run

1. Install Apache Hop (version 2.0 or higher)
2. Clone this repository
3. Import the pipeline into Apache Hop
4. Configure the CSV source with your data
5. Execute the pipeline

---

## 📝 Expected Outputs

| File | Description | Format |
|------|-------------|--------|
| `wine_data_output_IT.txt` | Raw Italian wine data | TXT |
| `france_aggregated_and_sorted.txt` | French data aggregated by region and sorted | TXT |

---

## 👨‍💻 Author

Cristiano Jacinto da Gama  
Project developed as an example of data pipeline implementation with Apache Hop.

---

## 📄 License

This project is licensed under the same license as Apache Hop.

---

## 🤝 Contributions

Contributions are welcome! Feel free to open issues or pull requests.
