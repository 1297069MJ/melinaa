# Hispanic Heritage Historical Data Explorer

A Streamlit classroom app for exploring World Bank historical indicators, editing a working data table, fitting polynomial models, calculating estimates, comparing countries, and studying functions/calculus.

## Country coverage

The selector includes all 20 Spanish-speaking sovereign countries: Argentina, Bolivia, Chile, Colombia, Costa Rica, Cuba, Dominican Republic, Ecuador, El Salvador, Equatorial Guinea, Guatemala, Honduras, Mexico, Nicaragua, Panama, Paraguay, Peru, Spain, Uruguay, and Venezuela. Puerto Rico is included separately as a territory. Brazil is included separately as a Latin American comparison and is not classified as Hispanic.

## Run locally

```bash
python -m pip install -r requirements.txt
python -m streamlit run app.py
```

## Deploy on Streamlit Community Cloud

1. Create a GitHub repository.
2. Upload `app.py` and `requirements.txt` (you may also upload this README and `sources.md`).
3. In Streamlit Community Cloud, create an app from the repository.
4. Select `app.py` as the main file and deploy.

## Deploy on Render

- Build command: `pip install -r requirements.txt`
- Start command: `streamlit run app.py --server.address=0.0.0.0 --server.port=$PORT`

## Important notes

- The app requests the 70 completed calendar years from current year minus 70 through current year minus 1. Actual coverage depends on the indicator and country.
- Missing World Bank values are omitted; the app does not invent replacement data.
- The polynomial degree must have at least degree + 1 distinct valid years.
- R-squared and MAE are in-sample metrics. A chronological holdout MAE is shown separately only when enough rows exist.
- Polynomial extrapolations can be unstable and are not validated forecasts or prediction intervals.
- GDP per capita is not average wealth or household income; crude birth rate is a rate, not a count; net migration is not an emigration count.
- Editing the table creates a user-modified scenario. Reset restores the source observations.
- The function lab accepts a restricted mathematical grammar and does not execute arbitrary Python code.

## Verification checklist

- Confirm the country selector includes all 20 Spanish-speaking sovereign countries plus Puerto Rico and Brazil comparison.
- Confirm World Bank data loads and reports its actual year coverage and observation count.
- Test an unavailable API response or offline connection; the app should show an error/no-data message and must not fabricate values.
- Edit a value, then use Reset to source.
- Try duplicate years, non-integer years, nonnumeric values, and invalid negative values for nonnegative indicators.
- Try a polynomial degree that exceeds available distinct years.
- Compare a single-year estimate with the same year in batch results.
- Change the degree, sample increment, display horizon, comparison countries, course mode, and function visibility controls.
- Download and open the CSV, XLSX, and PDF files.
- Review Streamlit logs if deployment fails.

## Limitations

This is a classroom analysis tool, not a validated forecasting system. It does not infer historical causes. Numerical calculus analysis for complicated expressions may be approximate or incomplete. Some countries/indicators may have sparse or unavailable observations in the World Bank database.
