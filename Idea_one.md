# 🏙️ City Recommendation System Based on Income and Preferences (Unsupervised + Recommender Systems)

### Overview  
As remote work, climate migration, and lifestyle flexibility become the norm, there's growing demand for intelligent, data-driven relocation tools. This project builds a **City Recommendation System** that helps users—especially **remote workers, families, and retirees**—discover ideal cities based on **income, lifestyle, cost-of-living tolerance, and preferences**.

---

### 🌍 Why It’s Marketable:
- **Remote Work Boom**: Millions are no longer tied to one location and want to relocate intelligently.
- **Affordability Crisis**: Rising rents and inflation make cost-aware recommendations a must.
- **Complex Trade-offs**: People juggle crime rates, climate, job markets, and amenities—this system simplifies the decision.
- **Monetizable Insights**: Real estate, job platforms, relocation services, and local governments benefit from the recommendation outputs.

---

### 🎯 Target Audience:
- **Remote Workers**: Seeking affordable, high-quality places to live and work.
- **Young Professionals & Families**: Prioritizing schools, healthcare, and career hubs.
- **Retirees**: Looking for affordable, safe, and pleasant communities.
- **Real Estate Platforms (e.g., Zillow, Redfin)**: Interested in recommendation engines for engagement.
- **Relocation Services (e.g., U-Haul, PODS)**: Potential partners for integrated leads.
- **Local Governments & Economic Development Agencies**: Keen on attracting newcomers.

---

### 💡 How It Works:

#### ✅ Input:
- **User Income**
- **Preferences**: Climate, urban/suburban, school quality, safety, job type
- **Lifestyle Tolerance**: Commute time, pollution, noise, density

#### 📊 Data Sources:
- **Cost of Living**: Numbeo, Zillow (rent, groceries, utilities, transport)
- **Quality of Life & Amenities**: Healthcare, education, entertainment density
- **Climate & Pollution**: NOAA, OpenWeatherMap, Numbeo Pollution Index
- **Crime Data**: Numbeo Crime Index, FBI
- **Job Markets**: BLS, LinkedIn, DoingBusiness.org
- **Housing & Taxes**: Rent trends, property and income tax data

---

### 🔧 Data Preparation:
- City-level joins using **FIPS codes / city-state pairs**
- **Numerical scaling** (e.g., StandardScaler for rent, AQI)
- **Missing value imputation** via KNN and regional medians
- **Encoding preferences** (e.g., hot/humid climate, suburban/rural)
- Creation of derived features (e.g., **Affordability Index** = income / cost index)

📦 **Libraries**: `pandas`, `numpy`, `sklearn`, `plotly`, `seaborn`, `matplotlib`

---

### 🤖 Modeling Components

#### 🌀 Unsupervised Learning (User Clustering)
- **KMeans** and **DBSCAN**: Group users based on lifestyle, income, and preference profiles.
- **Autoencoders**: Compress high-dimensional preference vectors before clustering.
- **PCA, t-SNE, UMAP**: Visualize user and city groupings.
- **Self-Organizing Maps (SOMs)**: Topological visualizations of user intent.

#### 🧭 Recommender System
- **Content-Based Filtering**: Match user vectors with city profiles using **cosine similarity**.
- **Collaborative Filtering** (if interactions available): Use **TruncatedSVD**, **LightFM**, etc.
- **Graph-Based Modeling (Optional)**: Model user-city-feature triplets with **Node2Vec**, **GraphSAGE**.
- **Hybrid Recommender**: Combine clustering, similarity, and collaborative filtering in a weighted ensemble.

---

### 📈 Forecasting Add-On
- **Future Cost Projections**: Forecast rent, wage, and tax trends using:
  - `ARIMA`, `Prophet`, or `XGBoost`
- **Stability Score**: Adds a time component to recommendations.

---

### 🧠 Interpretability

#### SHAP & LIME:
- Use **SHAP values** to explain why a city was chosen (e.g., affordability, job market).
- **LIME** for real-time local interpretability of recommendations.
- Visual breakdowns for users and stakeholders.

---

### 📐 Key Metrics:
- **Match Score (0–100)**: Overall relocation fit
- **Affordability Index**: Normalized cost-income ratio
- **Lifestyle Fit Score**: Climate, density, entertainment, healthcare
- **Stability Forecast**: Future viability based on cost projections
- **Cluster Cohesion Score**: Silhouette, Calinski-Harabasz, Davies-Bouldin

---

### 🧪 Example User Journey

#### Input:
- Income: **$85,000/year**
- Preferences: **Mild climate**, suburban, good schools, remote tech job opportunities, low crime

#### 🔝 Top 3 Cities:
1. **Raleigh, NC** – Booming tech market, excellent healthcare, strong affordability  
2. **Boise, ID** – Low crime, great environment, rising job opportunities  
3. **Madison, WI** – Great schools, cultural vibrancy, balanced cost of living

#### SHAP Breakdown:
- ✅ School Quality: 🟢 Strong Match  
- ⚖️ Climate: 🟡 Neutral Fit  
- 💸 Affordability: 🔴 Dominant Factor

---

### 📊 Evaluation

#### ✅ Strengths:
- Transparent, **interpretable**, personalized recommendations
- **Hybrid modeling** with clustering, embeddings, and filtering
- Time-aware forecasting integrated with static city data
- Partner-ready (real estate, relocation, local governments)

#### ⚠️ Limitations:
- Monthly refresh needed for job and rent data
- No feedback loop or user interaction modeling yet
- Some deep learning components (e.g., autoencoders) may reduce business interpretability
- Access to real-time APIs may require payment

---

### 🚀 Next Steps
- **Forecasting Expansion**: Use Prophet/XGBoost to forecast long-term affordability
- **Community Matching**: Add social fit using lifestyle and demographic data
- **Graph Engine**: Use graph embeddings for better context-aware suggestions
- **Gamified Quiz**: Buzzfeed-style quiz to convert soft traits into feature weights
- **Reinforcement Learning**: Long-term relocation journeys (e.g., move now, reevaluate in 3 years)
- **Interactive Dashboard**: Deploy API + real-time interface for users and partners

---

### 💼 Business Applications

| Stakeholder | Value |
|-------------|-------|
| 🏠 Real Estate Platforms | Smart city-matching = higher conversions |
| 🚛 Relocation Companies | Location leads = bundled service upsells |
| 🏛️ Local Governments | Use data to attract ideal residents |
| 💼 Job Boards | Match job listings with livable cities |
| 📈 Subscription Model | Premium reports and forecasts for consumers or B2B clients |

---

### 🧩 Conclusion

This **City Recommendation System** blends affordability data, lifestyle features, and intelligent modeling to offer **personalized, transparent, and future-aware** city suggestions.

It stands out by combining:
- **Clustering + Autoencoders** for user segmentation  
- **Content & Collaborative Filtering** for recommendations  
- **SHAP & Forecasting** for interpretability and long-term planning

Perfect for real estate tech, relocation apps, and civic planning—this is a robust, versatile project to showcase **advanced machine learning, explainable AI, and real-world impact.**

---
