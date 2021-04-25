climate_tech_company_classifier
==============================

A simple NLP classifier to help classify climate tech companies

Project Organization
------------

    ├── LICENSE
    ├── Makefile           <- Makefile with commands like `make data` or `make train`
    ├── README.md          <- The top-level README for developers using this project.
    ├── data
    │   ├── external       <- Data from third party sources.
    │   ├── interim        <- Intermediate data that has been transformed.
    │   ├── processed      <- The final, canonical data sets for modeling.
    │   └── raw            <- The original, immutable data dump.
    │
    ├── docs               <- A default Sphinx project; see sphinx-doc.org for details
    │
    ├── models             <- Trained and serialized models, model predictions, or model summaries
    │
    ├── notebooks          <- Jupyter notebooks. Naming convention is a number (for ordering),
    │                         the creator's initials, and a short `-` delimited description, e.g.
    │                         `1.0-jqp-initial-data-exploration`.
    │
    ├── references         <- Data dictionaries, manuals, and all other explanatory materials.
    │
    ├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
    │   └── figures        <- Generated graphics and figures to be used in reporting
    │
    ├── requirements.txt   <- The requirements file for reproducing the analysis environment, e.g.
    │                         generated with `pip freeze > requirements.txt`
    │
    ├── setup.py           <- makes project pip installable (pip install -e .) so src can be imported
    ├── src                <- Source code for use in this project.
    │   ├── __init__.py    <- Makes src a Python module
    │   │
    │   ├── data           <- Scripts to download or generate data
    │   │   └── make_dataset.py
    │   │
    │   ├── features       <- Scripts to turn raw data into features for modeling
    │   │   └── build_features.py
    │   │
    │   ├── models         <- Scripts to train models and then use trained models to make
    │   │   │                 predictions
    │   │   ├── predict_model.py
    │   │   └── train_model.py
    │   │
    │   └── visualization  <- Scripts to create exploratory and results oriented visualizations
    │       └── visualize.py
    │
    └── tox.ini            <- tox file with settings for running tox; see tox.readthedocs.io


--------
Stopping Criteria 
------------
- The prediction has to be performative enough that it actually saves me time compared to classifying companies manually (circa 100 startups per city, so for each prediction with high enough confidence to be automated, say >90%, would save me around 30-90 seconds per instance reading the description or reviewing the website to classify the company) 
- The classifier needs to go down to 2nd hierarchy (subdomain) to allow total automation but the accuracy at this level is less critical (tag suggestion is only a nice-to-have)
- The classifier does need to account for the long-tail of non/under-represented classes that are not in the label set, however this could be pushed if examples cannot be found. 
- There needs to be a way for me to focus just on the ones that need to be manually checked (e.g. model is still uncertain) and accept those where the model is confident 
- There needs to be an easy way for these suggestions to augment the collect data so what it practically saves me time in my workflow 

Todo
------------
- Define stopping-critiera [X]
- impliment basic classifier [X]
- assess issue areas with LIME 
- setup MLflow service to track experiments 
- improve data prep and cleaning 
- explore more sophisticated classifiers (Hugging face text-classifier)
- explore other techniques to improve model towards stopping-criteria
- extend to 2nd hierarchy (subdomain) and explore hierarchical model options 
- explore options for extending to tags (e.g. keyword analysis, topic modelling, word summarization) 
- create simple streamlit app to make it useful:
         -company text input -> prediction + probability
         - upload csv -> return filled csv
         - label feedback learning system?
- write core property-based testing 
- package/containerize and deploy 
