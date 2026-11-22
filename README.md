# sales-quantity-predictor

Random forest regression that predicts the quantity sold on a sales invoice line, with a Streamlit form to try it.

## Features

- `predictive_analytics.py`: training script. Cleans an invoice spreadsheet, encodes and scales features, trains a `RandomForestRegressor`, shows a feature importance plot and saves `random_forest_model.pkl`.
- `app.py`: Streamlit app with sidebar inputs (customer, salesman, amounts, item, territory, due date) and a Predict button that shows the predicted quantity.

## Tech stack

Python, pandas, scikit-learn, Streamlit, matplotlib, category_encoders.

## Project structure

```
app.py                     Streamlit app
predictive_analytics.py    training script
random_forest_model.pkl    trained model
requirements.txt
```

## Setup and run

1. `pip install -r requirements.txt` (the training script also needs `matplotlib`, `category_encoders` and `openpyxl`).
2. Run the app: `streamlit run app.py`
3. To retrain, place your invoice data as `data.xlsx` in the project folder (not included) and run `python predictive_analytics.py`.

No environment variables are needed.

## Usage

Fill the sidebar fields and press Predict. The app shows the predicted quantity and its rounded value.

## Status and limitations

- The training data is not in the repo, so retraining needs your own `data.xlsx` with the original column names (CustNo, Salesman, Qty, and so on).
- The app encodes and scales a single input row with fresh `LabelEncoder` and `MinMaxScaler` objects, so those values do not match the training transform. Predictions are not reliable.
- The app passes 15 columns while the training script saves a model fitted on 9 reduced features, so the pickled model may reject the input. Not verified here.
- The pickle file loads arbitrary code on open; only use a model you trust.
- Demo quality, no tests, no accuracy figures are reported.

## License

MIT
