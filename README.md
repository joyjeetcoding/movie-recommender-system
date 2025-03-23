# 🎬 MOVIE RECOMMENDATION SYSTEM

My first ML Project! 🚀

This system takes a movie name as input and recommends **five** similar movies based on matching tags such as **Directors, Actors, and Genre.**

## 📂 Datasets & Libraries Used

### 📌 Libraries
- **Pandas** → For data manipulation and preprocessing
- **Scikit-learn** → For vectorization and cosine similarity calculation

## 📂 Datasets
There are two datasets downloaded from **Kaggle.**

## 🛠 Steps to Build the Model

### 1️⃣ Merging Datasets
- Merged both datasets using the **movie title** as the common key.

### 2️⃣ Selecting Relevant Columns
- Kept only necessary columns: **id, title, keywords, cast, crew, overview, genres.**

### 3️⃣ Handling Missing Data
- Removed movies with **null values**.

### 4️⃣ Extracting Important Information
- Extracted **genre names** from the genre column.
- Extracted **keywords** from the keyword column.
- Took only the **first three actors** from the cast column.
- Extracted only the **director's name** from the crew column.

### 5️⃣ Preprocessing Data (Creating "Tags")
- Removed spaces in **genres, keywords, cast, and crew** to make them single words.
- **Why?** This prevents incorrect recommendations.
  - Example: A user searching for *Sam Worthington* shouldn't get results for *Sam Mendes*.
  - To avoid this, "Sam Worthington" is treated as a single word.

### 6️⃣ Creating a New DataFrame
- Final dataframe contains only **id, title, and tags**.

### 7️⃣ Applying Stemming
- Reduced words to their root form to improve similarity detection.
- Example:
  ```
  ability → ability  
  abilities → ability  
  actor → actor  
  actors → actor  
  dance → dance  
  dances → dance  
  ```

### 8️⃣ Vectorization & Distance Calculation
- Converted **tags into vectors**.
- Used the **Bag of Words** technique (removing stop words).
- Selected **5000 most frequent words**.

### 9️⃣ Choosing the Similarity Measure
- Used **Cosine Similarity** instead of Euclidean Distance.
- **Why?**
  - Euclidean distance works poorly in high dimensions.
  - Cosine similarity considers **angle difference** rather than direct distance.

### 🔟 Sorting Movies
- Sorted in **descending order** based on similarity.

### 1️⃣1️⃣ Limiting Recommendations
- Returned **top 5** most similar movies.

### 1️⃣2️⃣ Creating the Recommendation Function
- Function takes a **movie name as input** and suggests similar movies.

## 🌐 Frontend Integration
- Sent **movie data** to the frontend using `pickle`.
- Saved two `.pkl` files:
  1. **Processed movie data**
  2. **Similarity matrix**
- These `.pkl` files should be **copied to the frontend project folder** for usage.

## 🔗 Frontend Repository
[Click Here](https://github.com/joyjeetcoding/movie-recommender-system-frontend)
