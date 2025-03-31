# 🌆 City Recommendation System Based on Income and Preferences

---

### Overview

Remote work, rising housing costs, and growing lifestyle mobility have created demand for intelligent relocation tools. This system helps users—especially remote workers, retirees, and families—identify ideal cities based on their income, cost-of-living tolerance, climate, amenities, and personal preferences. 

---

### Business and Data Understanding

#### Business Problem

People are increasingly mobile but overwhelmed by scattered information across cost-of-living, quality of life, job markets, and amenities. They need a **personalized, data-driven tool** to help them make informed relocation decisions that align with their budget and lifestyle.

---

### Primary Stakeholders

- **Remote Workers**: Looking to relocate for affordability, climate, or quality of life.
- **Young Professionals & Families**: Seeking access to schools, healthcare, and job opportunities.
- **Retirees**: Want affordable, safe, and pleasant places to settle.
- **Real Estate Platforms (e.g., Zillow, Redfin)**: Want leads and engagement tools.
- **Relocation Services (e.g., U-Haul, PODS)**: Can integrate with recommendation outputs.
- **Local Governments & Chambers of Commerce**: Want to attract new residents and workers.

---

### Objective

Build a **personalized city recommendation engine** that:

- Matches users to cities based on **income, lifestyle, and personal preferences**
- Incorporates **cost of living, amenities, climate, safety, and job data**
- Offers **interpretable and transparent recommendations** for relocation
- Provides **monetizable insights** for business partners

---

### Data Understanding

#### Data Sources

🏠 **Cost of Living**: Numbeo, Zillow (rent, utilities, groceries, transportation)
- https://www.numbeo.com/cost-of-living/rankings_current.jsp
- https://www.numbeo.com/quality-of-life/rankings_current.jsp
- https://www.numbeo.com/traffic/rankings_current.jsp

🌤️ **Climate & Geography**: NOAA, OpenWeatherMap
- https://www.numbeo.com/pollution/rankings_current.jsp

🏥 **Amenities**: Hospital ratings, school rankings, entertainment density
- https://www.numbeo.com/health-care/rankings_current.jsp

🔒 **Safety & Crime**: Numbeo Crime Index, FBI crime stats
- https://www.numbeo.com/crime/rankings_current.jsp

💼 **Job Market**: BLS employment rates, LinkedIn job trends, industry presence
- https://archive.doingbusiness.org/en/rankings

💸 **Housing & Taxes**: Rent trends, local income tax, property tax data
- https://www.numbeo.com/property-investment/rankings_current.jsp

---

### Data Preparation Highlights

- Merged datasets by city-level keys (e.g., FIPS codes or city/state)
- Scaled numerical features (e.g., median rent, AQI) using `StandardScaler`
- Imputed missing values using `KNNImputer` and regional medians
- Encoded categorical preferences (e.g., climate type, urban/rural)
- Created composite indices (e.g., Affordability Index = income / cost index)

**Tools/Libraries**: `pandas`, `sklearn`, `numpy`, `matplotlib`, `seaborn`, `plotly`

---

### Modeling

#### Clustering (User Segmentation)

Goal: Group users by relocation preferences to offer community-style matching and context-aware city suggestions.

- **KMeans & DBSCAN**: Used for income-preference clustering
- **Dimensionality Reduction**: PCA, t-SNE, and UMAP for visualization
- **Autoencoders**: For compressing high-dimensional user and city data into latent features before clustering
- **Self-Organizing Maps (SOMs)**: To visualize user preference topologies

#### Recommendation Models

1. **Content-Based Filtering**:
   - Match user preferences with city attributes using cosine similarity
   - Personalized scores for affordability, safety, climate, and amenities

2. **Collaborative Filtering (Advanced)**:
   - If implicit or explicit interaction data is available, recommend cities liked by similar users using matrix factorization techniques (e.g., `TruncatedSVD`, `LightFM`)

3. **Graph-Based Recommendation (Optional)**:
   - Use graph embeddings (e.g., Node2Vec) to capture relationships between users, cities, and features

4. **Hybrid Recommender System**:
   - Combine clustering, content similarity, and collaborative filtering into a weighted ensemble for improved accuracy

5. **Future Cost Projection**:
   - Use time-series models (e.g., Linear Regression, ARIMA, or Facebook Prophet) to forecast rent, income, and tax trends for each city

---

### Interpretability & Metrics

#### Transparency Techniques

- **SHAP (SHapley Additive Explanations)**:
  - Applied to similarity and clustering outputs to explain **why** a city was recommended
  - Visual breakdown of feature contributions to recommendations

- **LIME**:
  - Used for local explanations in real-time city suggestions

#### Key Metrics

- **Match Score (0–100)**: Overall recommendation strength
- **Affordability Index**: (Income - Cost of Living) normalized
- **Lifestyle Fit Score**: Composite of climate, density, amenities
- **Stability Forecast**: Future cost projections based on trends
- **Cluster Cohesion Score**: Silhouette, Calinski-Harabasz, Davies-Bouldin

---

### Example Scenario

> **User Input**:  
Income: $85,000/year  
Preference: Mild climate, suburban, good schools, strong healthcare, remote tech job availability

> **Top 3 Recommendations**:
1. **Raleigh, NC** – Strong affordability, booming tech jobs, great healthcare  
2. **Boise, ID** – Low crime, clean environment, rising industry presence  
3. **Madison, WI** – Excellent schools, cultural amenities, moderate cost of living

> **SHAP Output**:  
Affordability: 🔴 (driving factor)  
Climate: 🟡 (neutral match)  
School Quality: 🟢 (strong match)

---

### Evaluation

#### Strengths

- Personalized, transparent recommendations
- Advanced modeling with clustering, autoencoders, and explainable AI
- Combines static data (e.g., crime, rent) with dynamic forecasts (e.g., job growth, housing trends)
- Actionable next steps (e.g., links to listings, partner services)

#### Limitations

- Real-time user feedback loop not yet integrated
- Cost and job data can lag (monthly updates recommended)
- May require premium APIs for accurate, real-time city and housing data
- Deep learning interpretability (e.g., autoencoders) may be more complex for business stakeholders

---

### Next Steps

- **Time-Series Expansion**:
  - Forecast rent, tax, and wage trends over 5–10 years using `Prophet`, `XGBoost`, etc.

- **Community Matching**:
  - Add optional “social fit” score (demographics, values, lifestyle)

- **Graph Recommendation Engine**:
  - Build graph structure with city-user-feature triplets and use Node2Vec or GraphSAGE

- **Gamified Relocation Quiz**:
  - Match personality and lifestyle traits to ideal cities

- **Reinforcement Learning (Long-Term Planning)**:
  - Use Q-Learning or Contextual Bandits to suggest multi-step relocation plans (e.g., move now, reevaluate in 2 years)

- **API + Dashboard Deployment**:
  - Real-time interactive dashboard for partners (real estate, relocation)

---

### Business Recommendations

📈 **Real Estate Platforms** → Offer smart city-matching to improve engagement  
🧳 **Relocation Services** → Integrate recommender to generate qualified leads  
🏛️ **Local Governments** → Use insights to attract target demographics  
💼 **Job Boards** → Pair job listings with ideal city suggestions  
📊 **Subscription Model** → Offer premium forecasting & personalized reports  

---

### Conclusion

This City Recommendation System bridges the gap between subjective lifestyle choices and hard cost-of-living data. It empowers individuals with transparent, data-driven relocation guidance—while offering scalable monetization opportunities for real estate, employment, and relocation stakeholders.

By combining clustering, deep embeddings, SHAP explainability, and forecasting models, the system provides a robust and flexible framework for advanced, interpretable, and personalized recommendations.

---
