# Hybrid Financial Stability Modeling: Integrating Batch and Online Learning Approaches

This repository contains a machine learning project that combines batch learning and online learning techniques to predict financial stability. By integrating a RandomForestClassifier (offline model) with an SGDClassifier (online model updated incrementally via partial_fit), the project demonstrates a robust and adaptable solution for classifying financial stability into three classes:

- **Financially Stable**
- **Moderately Stable**
- **Financially Unstable**

## Overview

The hybrid approach leverages:

- **Batch Learning:** Trains a RandomForestClassifier on the entire dataset to establish a strong baseline.
- **Online Learning:** Uses an SGDClassifier updated continuously with new data, making it ideal for real-time applications.
- **Visualization:** Comprehensive graphs and metrics (accuracy, classification reports, confusion matrices, and feature importance plots) for both models.

This project is ideal for showcasing both theoretical understanding and practical implementation of different learning paradigms—an excellent addition to any ML internship portfolio.

## Project Structure

The repository is organized as follows:

hybrid-financial-stability-model/ ├── data/
│ └── (dataset files, if applicable) ├── notebooks/
│ └── (Jupyter notebooks for experiments and API testing) ├── src/
│ ├── model_training.py # Script for training both batch and online models │ ├── api.py # Flask API for continuous online model updates │ └── visualization.py # Scripts for generating evaluation graphs ├── README.md # This file └── requirements.txt # List of dependencies (e.g., pandas, numpy, scikit-learn, matplotlib, seaborn, flask, joblib)

markdown
Copy
Edit

## Dataset and Feature Engineering

- **Dataset:**  
  The model uses a financial dataset (e.g., Indian finance data) loaded from a CSV file. Update the `csv_path` in the code as necessary.
  
- **Feature Engineering:**  
  - Creation of financial ratios (e.g., Debt-to-Income Ratio, Savings-to-Income Ratio) if the target column is missing.
  - Dropping of irrelevant columns.
  - Encoding of categorical variables (e.g., Occupation, City Tier).
  - Stratified train-test split and standardization using `StandardScaler`.

## Models

### Offline Model: RandomForestClassifier
- **Purpose:** Establish a baseline by training on the full dataset.
- **Evaluation:** Accuracy, classification report, confusion matrix, and feature importance (extracted from the model).

### Online Model: SGDClassifier
- **Purpose:** Demonstrates incremental learning by updating the model with new data batches using `partial_fit`.
- **Evaluation:** Accuracy, classification report, confusion matrix, and feature importance (using averaged absolute coefficients as a proxy).

## Visualizations

Separate visualizations are provided for both models:

- **Offline (Batch) Visualizations:**
  - Bar and pie charts displaying the distribution of financial stability classes (ground truth).
  - Feature importance plot from RandomForestClassifier.
  - Confusion matrix.
  
- **Online (Incremental) Visualizations:**
  - Bar and pie charts for the online model predictions.
  - Confusion matrix.
  - Feature importance plot based on averaged absolute coefficients from SGDClassifier.

Each graph is generated in its own figure with tight layouts and clear labels to ensure clarity.

## Web API Integration

A Flask API is implemented to update the online model continuously. The `/update` endpoint accepts JSON payloads with new data and labels, preprocesses the data using the pre-fitted scaler, and updates the SGDClassifier using `partial_fit`. This simulates a real-time data stream where the model learns continuously. (See `src/api.py` for implementation details.)

## Setup and Installation

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/yourusername/hybrid-financial-stability-model.git
   cd hybrid-financial-stability-model
Install Dependencies: Ensure you have Python 3 installed and run:

bash
Copy
Edit
pip install -r requirements.txt
Dependencies include: pandas, numpy, scikit-learn, matplotlib, seaborn, flask, joblib.

Dataset: Place your dataset in the data/ folder or update the csv_path in the source code accordingly.

Usage
Model Training and Evaluation:
Run the src/model_training.py script (or use the corresponding notebook in the notebooks/ folder) to train both the offline and online models, generate evaluations, and save visualizations.

API Testing:
Run the Flask API by executing src/api.py. For testing purposes (e.g., in a Kaggle notebook), use Flask’s test client or tools like Postman to simulate POST requests to the /update endpoint.

Results
Offline Model:
Achieves strong performance (e.g., 90%+ accuracy) with clear insights into feature importance and prediction performance.

Online Model:
Demonstrates adaptability through continuous updates and provides comparable evaluation metrics, with a clear view of how each feature influences predictions.

Future Work
API Enhancements:

Add authentication and security measures.

Integrate logging and error monitoring.

Model Improvements:

Explore advanced online learning techniques.

Implement adaptive scaling methods for continuous data streams.

Deployment:

Deploy the API on a cloud platform to handle real-world data streams.

Integrate with a front-end dashboard for real-time monitoring.

Contributing
Contributions are welcome! To contribute:

Fork the repository.

Create your feature branch: git checkout -b feature/YourFeature

Commit your changes: git commit -m 'Add some feature'

Push to the branch: git push origin feature/YourFeature

Open a pull request.

License
This project is licensed under the MIT License. See the LICENSE file for details.

yaml
Copy
Edit

---

This final README file is now well-organized and the project structure section is presented clearly without extraneous symbols. Feel free to adjust any sections as needed for your specific project details.
