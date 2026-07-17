 1. Ingestion & Initial Exploratory Assessment

**Automated Data Fetching:** The pipeline utilizes `pandas` to stream the raw Titanic dataset directly from a remote repository, ensuring reproducibility without needing local data downloads[cite: 1].
* **Structural Inspection:** Conducts programmatic checks using `.info()`, `.describe()`, and `.isnull().sum()` to map out data types, identify missing value distributions, and analyze distinct value cardinalities across categorical features[cite: 1]. The initial shape of the dataset stands at **891 rows and 15 attributes**[cite: 1].

### 2. Feature Pruning & Dimensionality Reduction
To prevent multicollinearity, optimize memory footprint, and improve model interpretability, the following pruning strategies were executed[cite: 1]:

* **Redundant Column Elimination:** 
  * `class` was removed as it perfectly duplicates `pclass` (Passenger Class)[cite: 1].
  * `embarked` (single-letter code) was removed in favor of `embark_town` (full text), eliminating duplicated data[cite: 1].
  * `alive` was dropped because it acts as a direct text proxy for the target label `survived`[cite: 1].
* **High-Nullity Dropping:** 
  * The `deck` column was entirely removed[cite: 1]. With over 50% of its records missing (`NaN`), any attempt at imputation would introduce massive bias into downstream models[cite: 1].

### 3. Smart Conditional Imputation (Age Feature)
Simply filling missing values with the overall global mean or median introduces artificial distortion. Instead, this pipeline implements a **stratified imputation strategy** for the `age` column based on its strong correlation with a passenger's socio-economic status (`pclass`)[cite: 1].

* **Socio-Economic Age Profiling:** Granular analysis of the dataset revealed distinct mean age variations across passenger classes[cite: 1]:
  * **1st Class (`pclass == 1`):** Mean Age $\approx 38.2$ years[cite: 1]
  * **2nd Class (`pclass == 2`):** Mean Age $\approx 29.8$ years[cite: 1]
  * **3rd Class (`pclass == 3`):** Mean Age $\approx 25.1$ years[cite: 1]
* **The Imputation Function:** A custom row-by-row function was engineered to dynamically target the 177 missing `age` records[cite: 1]. If a passenger's age is missing, the algorithm looks up their `pclass` and applies the corresponding localized median estimation ($38$ for 1st class, $30$ for 2nd class, and $25$ for 3rd class)[cite: 1].

### 4. Categorical Encoding & Final Polish
* **Residual Clean-up:** Rows with remaining, non-imputable missing values (e.g., minor missing values in `embark_town`) were dropped, yielding a pristine dataset of **889 high-fidelity passenger profiles**[cite: 1].
* **Feature Transformation:** Categorical text strings—such as `sex`—were transformed using One-Hot Encoding (`pd.get_dummies`), converting qualitative features into binary numeric matrices ($0$ or $1$) required by mathematical machine learning frameworks[cite: 1].

---

## Dataset Layout Post-Cleaning

After executing the pipeline, the resulting dataframe properties are structured as follows:

| Attribute | Data Type | Imputation Applied | Purpose |
| :--- | :--- | :--- | :--- |
| `survived` | Integer (0 or 1) | None | **Target Variable** (Ground Truth) |
| `pclass` | Integer (1, 2, or 3) | None | Predictive Feature (Socio-economic Class) |
| `sex` | Object / Encoded | None | Predictive Feature (Gender) |
| `age` | Float | **Class-Stratified Median**[cite: 1] | Predictive Feature (Continuous Demographics) |
| `sibsp` | Integer | None | Predictive Feature (Number of Siblings/Spouses aboard) |
| `parch` | Integer | None | Predictive Feature (Number of Parents/Children aboard) |
| `fare` | Float | None | Predictive Feature (Ticket Price Paid) |
| `embark_town`| Object / Encoded | Row Drop (Minor)[cite: 1] | Predictive Feature (Port of Embarkation) |

---

## Setup & Execution

### Prerequisites
Ensure you have Python 3.8+ installed. You can set up the environment and dependencies using the commands below:

```bash
# Clone the repository
git clone [https://github.com/YOUR-USERNAME/YOUR-REPO-NAME.git](https://github.com/YOUR-USERNAME/YOUR-REPO-NAME.git)
cd YOUR-REPO-NAME

# Install required data processing libraries
pip install pandas jupyter
