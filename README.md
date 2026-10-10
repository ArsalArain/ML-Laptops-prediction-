# Laptop Price Prediction

A machine learning project that predicts the price of a laptop (in euros) from its specifications such as brand, RAM, storage, CPU, GPU, screen and weight.

## Dataset

- **File:** `Laptop.csv` (1,303 laptops, 13 columns, no missing values or duplicate rows)
- **Target:** `Price_euros (Target)`
- **Original columns:** `laptop_ID`, `Company`, `Product`, `TypeName`, `Inches`, `ScreenResolution`, `Cpu`, `Ram`, `Memory`, `Gpu`, `OpSys`, `Weight`, `Price_euros (Target)`

## Project Workflow

1. **Data cleaning:** removed units from `Ram` (GB) and `Weight` (kg), checked for nulls and duplicates.
2. **Feature engineering:**
   - Screen: extracted `Touchscreen`, `IPS`, and calculated `ppi` (pixels per inch) from resolution and screen size.
   - CPU: extracted CPU brand, speed and model.
   - GPU: extracted GPU brand and model.
   - Storage: split `Memory` into `SSD`, `HDD`, `Hybrid` and `Flash_Storage` capacities, including laptops with two drives.
   - Operating system: grouped into `Windows`, `Mac` and `Other`.
3. **Encoding:** one-hot encoding for categorical features.
4. **Modelling:** trained and compared several regression models.
5. **Prediction:** predicts the price of a new laptop from its specifications.

## Results

| Model | R² | Mean Absolute Error |
|---|---|---|
| Linear Regression | 0.79 | ~€205 |
| KNN Regressor | 0.36 | ~€389 |
| Random Forest (basic) | 0.80 | ~€198 |
| Extra Trees (improved) | 0.82 | ~€172 |
| Random Forest (improved) | 0.85 | ~€168 |
| **CatBoost (improved)** | **0.85** | **~€158** |

The first three models were evaluated on a single 80/20 train-test split. The improved models were evaluated with 5-fold cross-validation, which gives a more reliable estimate.

**Best model:** CatBoost, with the lowest average error (about €158) and R² of 0.85.

## Technologies Used

- Python
- NumPy, Pandas
- Matplotlib, Seaborn
- Scikit-learn
- CatBoost
- Jupyter Notebook

## How to Run

1. **Clone the repository**
   ```bash
   git clone https://github.com/ArsalArain/ML-Laptops-prediction-.git
   cd ML-Laptops-prediction-
   ```

2. **(Optional) Create a virtual environment**
   ```bash
   python -m venv .venv
   .venv\Scripts\activate
   ```

3. **Install the requirements**
   ```bash
   python -m pip install -r requirements.txt
   ```

4. **Open the notebook**
   ```bash
   jupyter notebook ML_Project.ipynb
   ```
   Then run all cells from top to bottom. Make sure `Laptop.csv` is in the same folder as the notebook.

## Project Structure

```
ML-Laptops-prediction-/
├── ML_Project.ipynb    # Main notebook (cleaning, features, models)
├── Laptop.csv          # Dataset
├── requirements.txt    # Python dependencies
└── README.md
```

## Author

**Arsal Arain**
GitHub: [ArsalArain](https://github.com/ArsalArain)
