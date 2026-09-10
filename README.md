🍽️ Restaurant Recommendation System
A machine learning–powered restaurant recommendation app built with Python, scikit-learn, pandas, and Gradio. Instead of predicting a single score for one restaurant, this app lets users set their preferences (cuisine, budget, dietary needs, minimum rating, distance) and returns a ranked list of real matching restaurants from the dataset — with a live, interactive UI deployable straight from Google Colab.
📌 Overview
This project trains a Random Forest Regressor to model a restaurant's RecommendationScore from its attributes (rating, taste, quality, service, value for money, price, distance, reviews, dietary flags, and category). The trained model is evaluated with standard regression metrics, and the dataset itself is then used to power an interactive Gradio recommendation interface — users type in their preferences and get back a ranked table of restaurants, led by name, with a highlighted "Top Pick" summary.
✨ Features
	•	📂 Flexible dataset upload — auto-detects delimiter (comma/tab) and header presence, no manual file renaming required.
	•	🧹 Data cleaning — duplicate removal and missing-value checks before training.
	•	🤖 ML pipeline — ColumnTransformer + OneHotEncoder for categorical features, RandomForestRegressor for the numeric target, wrapped in a single scikit-learn Pipeline.
	•	📊 Model evaluation — MAE, RMSE, and R² reported on a held-out test set.
	•	🎛️ Interactive recommender UI — typed numeric inputs (not sliders) for rating/price/distance thresholds, dropdowns for cuisine and dietary preferences, a collapsible "Dietary Preferences" section, and a styled Top Pick summary card.
	•	🌐 One-click public sharing — launches with share=True for an instant public Gradio link.
  restaurant-recommendation-system/
├── README.md
├── requirements.txt
├── .gitignore
├── notebook/
│   └── Restaurant_Recommendation_System.ipynb
└── data/
    └── (place your dataset CSV here — not included in the repo)
📋 Dataset
The notebook expects a CSV/TSV file with the following columns:
|Column             |Type                |Description                                        |
|-------------------|--------------------|---------------------------------------------------|
|Restaurant         |text                |Restaurant name                                    |
|Food               |text                |Dish/food item                                     |
|Category           |categorical         |Cuisine category (e.g. Chinese, Mughlai, Thai)     |
|Price              |numeric             |Price of the item                                  |
|Rating             |numeric             |Overall restaurant rating                          |
|Taste              |numeric             |Taste score                                        |
|Quality            |numeric             |Quality score                                      |
|Service            |numeric             |Service score                                      |
|ValueForMoney      |numeric             |Value-for-money score                              |
|Distance           |numeric             |Distance to restaurant                             |
|Reviews            |numeric             |Number of reviews                                  |
|Open24Hours        |categorical (Yes/No)|Whether open 24 hours                              |
|Vegetarian         |categorical (Yes/No)|Vegetarian option available                        |
|LowSugar           |categorical (Yes/No)|Low-sugar option available                         |
|LowCalorie         |categorical (Yes/No)|Low-calorie option available                       |
|AllergyFriendly    |categorical (Yes/No)|Allergy-friendly option available                  |
|RecommendationScore|numeric             |**Target variable** — used for training and ranking|
The dataset is not bundled in this repo — upload your own file when prompted in the notebook.
🚀 Getting Started
Option 1 — Run on Google Colab (recommended)
	1.	Open the notebook in Google Colab.
	2.	Run the cells in order from top to bottom.
	3.	When prompted, use the file picker to upload your dataset (CSV or TSV, any filename).
	4.	After training and evaluation, the final cell launches the Gradio app with a public shareable link.
Option 2 — Run locally

git clone https://github.com/<your-username>/restaurant-recommendation-system.git
cd restaurant-recommendation-system
pip install -r requirements.txt
jupyter notebook notebook/Restaurant_Recommendation_System.ipynb

Then run all cells sequentially. Note: the notebook's upload cell uses google.colab.files.upload(), so if running locally in classic Jupyter, swap that cell for an ipywidgets.FileUpload widget or a direct pd.read_csv("your_file.csv") call.
🧠 Model Details
	•	Algorithm: RandomForestRegressor
	•	Hyperparameters: n_estimators=200, max_depth=10, random_state=42, n_jobs=-1
	•	Preprocessing: numeric features passed through unchanged; categorical features one-hot encoded with handle_unknown="ignore"
	•	Train/test split: 80/20, random_state=42
	•	Evaluation metrics: MAE, RMSE, R² (printed in the notebook after training)
  🛠️ Tech Stack
	•	Python 3
	•	pandas / numpy
	•	scikit-learn
	•	Gradio

  📄 License
This project is licensed under the MIT License — see the LICENSE file for details.


    
