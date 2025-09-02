# ETL Project

This repository demonstrates a simple **ETL (Extract, Transform, Load)** pipeline built with Python.

## Requirements

* Python 3.9+
* pandas
* numpy

Install dependencies:

```bash
pip install -r requirements.txt
```

## Clone and Setup

To use this project, clone the repository:

```bash
git clone https://github.com/aguchhait-stack/etl_1.git
cd etl_1
```

Create a virtual environment (optional but recommended):

```bash
python -m venv venv
source venv/bin/activate   # On macOS/Linux
venv\Scripts\activate      # On Windows
```

Install dependencies:

```bash
pip install -r requirements.txt
```

## Usage

Run the Jupyter Notebook to execute the ETL steps:

```bash
jupyter notebook etl_pipeline.ipynb
```

Or run the Python script version (if available):

```bash
python etl_pipeline.py
```

## Data

Sample CSV files for dimensions and fact tables are provided in the repository for testing the ETL process.

## Contributing

Feel free to fork this repository and submit pull requests with improvements or bug fixes.

## License

This project is licensed under the MIT License.
