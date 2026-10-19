# Pandas_Cleaning_project
# 📞 Customer Call List Data Cleaning Project

An end-to-end data cleaning and preparation pipeline built using **Python** and **Pandas**. This project takes a messy, unformatted customer call list spreadsheet and transforms it into a clean, standardized, and production-ready dataset optimized for a call center campaign.

---

## 🛠️ Tech Stack & Libraries
* **Python 3.11+**
* **Pandas** (Data manipulation and cleaning)
* **Openpyxl** (Excel file reading/writing engine)

---

## 🧹 Data Cleaning Pipeline & Steps

The raw dataset contained typical real-world data quality issues. The cleaning notebook (`data_cleaning.ipynb`) performs the following operations:

1. **Duplicate Removal:** Dropped duplicate customer records to ensure each contact appears only once.
2. **Column Dropping:** Removed unnecessary metadata columns (`Not_Useful_Column`) to declutter the dataset.
3. **Text Standardization:** Cleaned messy formatting in the `Last_Name` column by stripping trailing punctuation characters (`/`, `.`, `_`).
4. **Phone Number Formatting:** 
   * Converted values to strings and used regular expressions (`regex=True`) to strip all non-digit characters.
   * Standardized 10-digit phone numbers into a clean, uniform format (`XXX-XXX-XXXX`).
   * Safely handled missing phone numbers using boolean masking (`.notna()`) to prevent data corruption.
5. **Address Splitting:** Split the single `Address` string into separate, organized columns (`Street_Code`, `State`, and `Postal_Code`) using `.str.split(n=2, expand=True)`.
6. **Flag Standardization:** Standardized inconsistent boolean-like response columns (`Paying Customer`, `Do_Not_Contact`) into uniform single-letter codes (`Y`/`N`).
7. **Missing Value & Filtering Logic:**
   * Filled missing flags and cleaned up null values.
   * Filtered out any records where customers explicitly opted out (`Do_Not_Contact == 'Y'`).
   * Dropped rows missing critical contact details (phone numbers).
8. **Exporting:** Saved the final cleaned dataset into a brand new Excel file (`cleaned_customer_call_list.xlsx`).

---

## 📂 Project Structure
```text
├── data_cleaning.ipynb          # Jupyter Notebook containing the step-by-step cleaning workflow
├── Customer Call List.xlsx      # The original raw dataset
└── cleaned_customer_call_list.xlsx # The final polished dataset ready for production
