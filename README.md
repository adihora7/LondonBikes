# London Bikes — Data Preparation

This project downloads and prepares the "London Bike Sharing" dataset for analysis and Tableau visualizations.

**Contents**
- Notebook: `london_bikes.ipynb` — data download, cleaning, and export to Excel.

## Dataset
The notebook downloads `hmavrodiev/london-bike-sharing-dataset` from Kaggle using the Kaggle API.

## Requirements
See [requirements.txt](requirements.txt) for the Python packages used.

## Setup
1. Install Python 3.8+.
2. Install project dependencies:

```powershell
python -m pip install -r requirements.txt
```

3. Configure the Kaggle API if you plan to download the dataset programmatically:
   - Create an API token via https://www.kaggle.com/ > Account > "Create API Token". This downloads `kaggle.json`.
   - Place `kaggle.json` in `%USERPROFILE%\.kaggle\kaggle.json` (create the `.kaggle` folder) and set permissions so it's not world-readable.

Alternative: download the dataset manually from Kaggle and put the ZIP file in the project folder.

## Running the notebook
Open the notebook in Jupyter and run cells in order. Key steps performed by the notebook:
- Download dataset with the Kaggle CLI (`!kaggle datasets download -d hmavrodiev/london-bike-sharing-dataset`) or use a local ZIP.
- Extract ZIP and read `london_merged.csv` into a pandas DataFrame.
- Clean/rename columns and export final DataFrame to Excel.

### Notes about writing Excel files
Pandas needs an Excel writer engine to save `.xlsx` files. If you see errors like "No module named 'openpyxl'" or permission errors, try:

```python
# install the engine
python -m pip install openpyxl
# then in the notebook
bikes.to_excel('london_bikes_final.xlsx', sheet_name='Data', engine='openpyxl')
```

If you get a permission error, close the file in Excel or write to a different filename.

## Outputs
- `london_bikes_final.xlsx` — final dataset exported from the notebook.

- Analysis Overview

<img width="1366" height="769" alt="Visual Showcase" src="https://github.com/user-attachments/assets/3f356c1d-ac21-4c31-bf4f-b45ed3d80769" />


## Troubleshooting
- Kaggle CLI not found: ensure the Python `Scripts` folder containing `kaggle.exe` is on your PATH or run `python -m pip install --user kaggle` and add the user Scripts folder to PATH.
- `to_excel` errors: see the Notes above (install `openpyxl` or `XlsxWriter`, ensure file not open).

## License
Project materials are provided as-is. See the Kaggle dataset page for dataset licensing information.
