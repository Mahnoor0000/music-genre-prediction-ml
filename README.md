#  Spotify Genre Classifier

This project predicts the **broad music genre** of songs (Pop, Rock, Hip-Hop/Rap, Dance/Electronic, Other) based on audio-style features such as **tempo, energy, danceability, acousticness, valence, etc.**  

The dataset used is a collection of top Billboard/Spotify tracks with metadata features.  

---

##  Project Workflow

### 1. Data Preparation
- Loaded dataset `spotify_top_music.csv`  
- Renamed columns for clarity:  
  - `top genre → genre`  
  - `nrgy → energy`  
  - `dnce → danceability`  
  - `spch → speechiness`  
  - `pop → popularity`  
- Converted `year` to integer values  
- Removed duplicate/extra columns  
- Simplified genres into **5 broad buckets**:  
  - Pop  
  - Rock  
  - Hip-Hop/Rap  
  - Dance/Electronic  
  - Other  

### 2. Exploratory Data Analysis (EDA)
- Checked distributions of numerical features  
- Detected outliers with **IQR method** (duration, bpm)  
- Visualized trends in features across years  
- Examined popularity vs energy/danceability  

### 3. Modeling
- **Baseline Model:** Logistic Regression (multinomial, with scaling)  
  - Accuracy: ~0.21 → ~0.40 after cleaning  
  - Too low; couldn’t capture nonlinear feature interactions  

- **Improved Model:** Random Forest Classifier 🌳  
  - Accuracy: ~0.80 on hold-out set  
  - Handles nonlinearities better  
  - Provides feature importance insights  

### 4. Prediction Function
- Added a function that takes **user input** (year, bpm, energy, etc.) and outputs the predicted genre.  
- Interactive cell included in the notebook so users can try their own values.  

---

##  Results
- Logistic Regression was too simple, struggled with overlapping genres.  
- Random Forest improved performance significantly, but:  
  - Still not perfect.  
  - Accuracy depends heavily on **feature engineering** and **dataset size**.  

---

##  Next Steps / Open to Contributions
- Add **more features** (e.g., Spotify API: key, mode, instrumentalness, explicit flag, streaming stats).  
- Try **advanced models** like Gradient Boosting (XGBoost, LightGBM, CatBoost).  
- Tune hyperparameters more systematically (RandomizedSearchCV / GridSearchCV).  
- Explore dimensionality reduction (PCA, t-SNE) for visualization.  
- Improve outlier handling and data balancing.  

---
