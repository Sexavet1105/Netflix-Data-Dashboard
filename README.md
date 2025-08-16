# 📊 Netflix Movies and TV Shows Dataset Analysis

## 📌 About this Dataset  
Netflix is one of the most popular media and video streaming platforms.  
- Over **8000 movies and TV shows** are available on Netflix.  
- As of **mid-2021**, Netflix has **200M+ subscribers globally**.  
- This dataset (from Kaggle) contains listings of all the movies and TV shows available on Netflix, with details such as:  
  - Cast  
  - Director  
  - Ratings  
  - Release year  
  - Duration  
  - Country  
  - Date added  

---

## 🎯 Tasks
1. Perform **network analysis of actors and directors** to find interesting insights.  
2. Analyze whether **Netflix has focused more on TV Shows than Movies in recent years**.  

---

## 🧹 Data Cleaning  

The dataset contains **missing (NaN) values** in several columns.  

### 🔎 Null Value Report
| Column     | NaN Count | NaN %  |
|------------|-----------|--------|
| Director   | 2634      | 29.91% |
| Cast       | 825       | 9.37%  |
| Country    | 831       | 9.44%  |
| Date Added | 10        | 0.11%  |
| Rating     | 4         | 0.05%  |
| Duration   | 3         | 0.03%  |

---

### 🛠 Code for Cleaning NaN Values
```python
# Remove leading/trailing whitespaces in object type columns
df[df.select_dtypes(include=['object']).columns.tolist()] = \
    df[df.select_dtypes(include=['object']).columns.tolist()].apply(lambda a: a.str.strip())

# Drop rows where 'date_added', 'duration', or 'rating' are missing
df = df.dropna(subset=['date_added', 'duration', 'rating'])

# Convert 'date_added' to datetime format
df['date_added'] = pd.to_datetime(df['date_added'])

# Fill missing values in 'cast', 'country', and 'director' with 'Unknown'
df[['cast', 'country', 'director']] = df[['cast', 'country', 'director']].fillna('Unknown')
```

## 📊 Dashboard Insights

### 🎬 Focus on Movie Production
Netflix has predominantly focused on **movies** over TV shows.  
- The chart *“Count of type by release_year and type”* clearly shows that the number of movies added each year **significantly outpaces** the number of TV shows.  

---

### 📈 Peak Movie Releases (2017–2018)
- Movie releases saw a **dramatic increase** from 2016 to 2017, reaching a peak of **640 titles** in 2017.  
- In 2018, the number stayed high with **632 titles**.  
- After 2018, however, the number of new movies began to **decline**.  

---

### 🎥 Prolific Directors on the Platform
- The *“Count of cast by director”* bar chart highlights directors with the **most content available** on Netflix.  
- Top three directors are:  
  - **Raúl Campos** → 18 titles  
  - **Marcus Raboy** → 15 titles  
  - **Jay Karas** → 14 titles  
- This suggests that Netflix has frequently **collaborated with or acquired content** from these directors.  

---

### 📺 Steady but Lower TV Show Growth
- TV shows have seen a **slow but steady growth** over time.  
- From only **3 shows in 2012** to **33 shows in 2020**, the increase is visible.  
- However, the number of TV shows still remains **significantly lower** compared to movies.  

---

### 🎛 Content Filtering Options
The dashboard provides interactive filtering options, allowing users to explore content by:  
- **Type** → Movie or TV Show  
- **Ratings** → G, NC-17, NR, PG, etc.  
- **Categories/Genres** → *Classic Movies*, *Documentaries*, etc.  

This enables a more **granular and customized analysis** of the Netflix library.  

---

### 📌 Summary
- Netflix has shown a **historical emphasis on movies**, especially with a surge in the late **2010s**.  
- While **TV show production is growing**, it remains **much slower** compared to movies.  
- A select group of **directors contribute a significant amount** of content to the platform.  

---






