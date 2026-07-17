# 📊 Ecommerce Customer Spending Prediction using Linear Regression

## 📌 Project Overview

This project builds a **Machine Learning Regression Model** to predict a customer's **Yearly Amount Spent** based on their online shopping behavior. The model is developed using **Python**, **Pandas**, **Matplotlib**, **Seaborn**, and **Scikit-learn**.

The notebook includes data exploration, visualization, model training, prediction, and evaluation using **Linear Regression**.

---

## 🎯 Problem Statement

Predict the **Yearly Amount Spent** of an ecommerce customer using the following features:

* Average Session Length
* Time on App
* Time on Website
* Length of Membership

---

## 📂 Dataset

The project uses the **Ecommerce Customers** dataset containing customer behavior and spending information.

### Features

* Avg. Session Length
* Time on App
* Time on Website
* Length of Membership

### Target Variable

* Yearly Amount Spent

---

## 🛠️ Technologies Used

* Python
* NumPy
* Pandas
* Matplotlib
* Seaborn
* Scikit-learn
* Google Colab

---

## 📈 Project Workflow

### 1. Import Libraries

* NumPy
* Pandas
* Matplotlib
* Seaborn

### 2. Load Dataset

* Import the Ecommerce Customers dataset
* Display sample records
* Explore dataset information

### 3. Exploratory Data Analysis (EDA)

Performed:

* Dataset overview
* Statistical summary
* Missing value check
* Joint plots
* Pair plots
* Linear regression plots

### 4. Feature Selection

Input Features (`X`):

* Avg. Session Length
* Time on App
* Time on Website
* Length of Membership

Target (`y`):

* Yearly Amount Spent

### 5. Train-Test Split

The dataset is divided into:

* 70% Training Data
* 30% Testing Data

### 6. Model Building

Algorithm Used:

* Linear Regression

Steps:

* Create the model
* Train using training data
* Learn regression coefficients

### 7. Prediction

The trained model predicts the yearly spending for unseen customer data.

### 8. Visualization

Model performance is visualized using a scatter plot comparing:

* Actual Values
* Predicted Values

---

## 📊 Machine Learning Algorithm

**Linear Regression**

Linear Regression is a supervised learning algorithm used to predict continuous numerical values.

---

## 📁 Project Structure

```text
ml_prediction.ipynb
README.md
Ecommerce Customers.csv
```

---

## ▶️ How to Run

1. Clone the repository.
2. Install the required libraries:

```bash
pip install numpy pandas matplotlib seaborn scikit-learn
```

3. Open the notebook:

```bash
jupyter notebook ml_prediction.ipynb
```

or run it in Google Colab.

---

## 📌 Future Improvements

* Perform feature engineering
* Evaluate the model using MAE, MSE, RMSE, and R² Score
* Save the trained model using Pickle or Joblib
* Build a web application using Flask or Streamlit
* Deploy the model on a cloud platform

---

## 📚 Learning Outcomes

Through this project, I learned:

* Data loading and preprocessing
* Exploratory Data Analysis (EDA)
* Data visualization with Seaborn and Matplotlib
* Feature selection
* Train-test splitting
* Building a Linear Regression model
* Making predictions
* Visualizing model performance

---


