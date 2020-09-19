Personality Type Nicotine Consumption Risk Assessment
==============================

According to the Centers for Disease Control and Prevention (CDC) smoking is the leading cause of preventable deaths in the United States. Not only is smoking very detrimental to one's health, smoking is also a very addictive. In an attempt to reduce the number of deaths attributed to smoking, this project aims to help anti-substance abuse organizations identify people who are smokers or are at high risk of picking up the habit based on their personality profiles.

Project Organization
------------

    ├── LICENSE
    ├── README.md          <- The top-level README for developers using this project.
    ├── data
    │   ├── interim        <- Intermediate data that has been transformed.
    │   │   └── drug_consumption.csv
    │   ├── processed      <- The final, canonical data sets for modeling.
    │   │   └── drug_consumption_pp.csv
    │   └── raw            <- The original, immutable data dump. Retrieved from: https://archive.ics.uci.edu/ml/datasets/Drug+consumption+%28quantified%29
    │       └── drug_consumption.data
    │
    │
    ├── notebooks          <- Jupyter notebooks. Naming convention is a number (for ordering),
    │   ├── 1.0-fa-data-wrangling.ipynb
    │   ├── 2.0-fa-exploratory-data-analysis.ipynb
    │   ├── 3.0-fa-pre-processig-and-modeling.ipynb
    │   └── 4.0-fa-modeling.ipynb
    │                    
    │
    ├── references         <- Data dictionaries, manuals, and all other explanatory materials.
    │
    ├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
    │   └── figures        <- Generated graphics and figures to be used in reporting
    │
    │
    └── src                <- Source code for use in this project.
        ├── __init__.py    <- Makes src a Python module
        │
        ├── data           <- Scripts to download or generate data
        │   └── make_dataset.py
        │
        ├── features       <- Scripts to turn raw data into features for modeling
        │   └── build_features.py
        │
        ├── models         <- Scripts to train models and then use trained models to make
        │   │                 predictions
        │   ├── predict_model.py
        │   └── train_model.py
        │
        └── visualization  <- Scripts to create exploratory and results oriented visualizations
            └── visualize.py
    


--------

<p><small>Project based on the <a target="_blank" href="https://drivendata.github.io/cookiecutter-data-science/">cookiecutter data science project template</a>. #cookiecutterdatascience</small></p>
