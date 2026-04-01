

### 1. Business Problem
Music streaming platforms need to understand:
- User listening behavior across time  
- Emotional preferences in music consumption  
- Engagement patterns for better recommendations  

The goal is to convert raw listening data into **actionable insights for personalization and retention**.

---

### 2. Data Collection
- Extracted Spotify listening history  
- Retrieved track-level features (energy, valence) using Spotify API  

---

### 3. Data Preprocessing (KNIME)
- Combined multiple datasets using Joiner nodes  
- Cleaned and filtered relevant columns  
- Handled missing feature values (excluded ~700 tracks without API data)  
- Aggregated and structured data for analysis  

---

### 4. Feature Engineering
- Created time-based features:
  - Time of Day, Day Name, Month Name, IsWeekend  
- Derived **Emotion Labels** using energy and valence:
  - Dark/Intense  
  - Happy/Euphoric  
  - Calm/Peaceful  
  - Sad/Melancholic  

👉 This step transforms raw data into **behaviorally meaningful segments**

---

### 5. Data Modeling
- Built a denormalized dataset for fast analytical queries  
- Combined behavioral + emotional + temporal features  
- Optimized for dashboard performance  

---

### 6. Dashboard Analysis

#### User Behavior & Emotional Profile
- High average energy (~0.73) indicates preference for intense music  
- Majority of tracks fall under high-energy emotional categories  

#### Time-Based Patterns
- Peak listening: Morning & Early Afternoon  
- Low activity: Late Night  

#### Monthly Trends
- Listening increases mid-year and stabilizes  
- No extreme fluctuations → consistent behavior  

#### Weekly Patterns
- Minimal variation across days  
- Slightly higher weekday engagement → routine-driven usage  

---

### 7. Recommendation Logic (SQL-Based)

A recommendation layer was built using SQL:

- Applied `ROW_NUMBER()` window function  
- Partitioned data by **emotion label**  
- Ranked tracks based on **similarity score**  

👉 Output:
- Top N tracks per emotional category  
- Emotion-based personalized recommendations  

Example logic:
- If user prefers "Dark/Intense" → recommend top-ranked tracks in that category  

---

### 8. Business Solution

This project enables streaming platforms to:

#### 🎯 Personalization
- Recommend songs based on **emotional preference**, not just popularity  

#### ⏰ Time-Based Targeting
- Suggest high-energy playlists during peak hours  
- Suggest calm playlists during low-activity periods  

#### 🔁 Retention Strategy
- Identify repeat listening behavior  
- Push similar tracks to increase session time  

#### 🎧 Content Strategy
- Focus on niche and mid-popularity tracks  
- Avoid over-reliance on mainstream trends  

---

### 9. Key Outcome

The analysis shows that:

- User behavior is **preference-driven, not trend-driven**  
- Emotional consistency plays a major role in listening patterns  
- Combining time + emotion + behavior enables **strong recommendation systems**  

👉 This creates a foundation for **next-gen personalized music experiences**
