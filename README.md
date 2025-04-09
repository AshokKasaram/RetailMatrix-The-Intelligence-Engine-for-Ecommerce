# RetailMatrix : The Intelligence Engine for Ecommerce

This project is a complete, end-to-end data science solution built using the **UCI Online Retail Dataset**. As an aspiring data scientist, I wanted to showcase not just technical skills but the ability to think like a product owner — transforming raw data into real business outcomes.

I focused on building an analytics and machine learning pipeline that starts with a messy dataset and ends with a working prediction tool, covering everything in between: analysis, recommendations, segmentation, modeling, and deployment.

---

## 🎯 Business Objective & Key Questions

The dataset contains over 500,000 transactions from an online retail store. My goal was to extract insights and build systems that would help a business understand its customers, products, and markets better.

### Key Business Questions I Answered:
1. Who are the most valuable customers?
2. Which products are best sellers or drive the most revenue?
3. When are sales happening — which days, months, or hours?
4. Which countries are the most profitable markets?
5. Can I group customers into behavioral segments?
6. Can I recommend relevant products to customers?
7. Can I predict if a customer will reorder an item?
8. Can I deploy this into a real-time interface that a business user can use?

---

## 📦 1. Data Loading & Understanding

I began by loading and profiling the dataset, which includes:
- Over 541,000 transaction records
- Key fields like invoice number, product code, description, quantity, date, unit price, customer ID, and country

I classified columns into categorical and numerical, analyzed missing values, and summarized each column's unique values. This helped me understand data types, quality, and complexity.

> **Why this matters:** I needed to understand the structure and limitations of the data to plan cleaning, feature extraction, and modeling.

---

## 🧼 2. Data Cleaning

I cleaned the data by:
- Removing rows with missing customer IDs (essential for tracking behavior)
- Excluding canceled orders (identified by invoice numbers starting with 'C')
- Filtering out negative or zero quantities and prices
- Dropping duplicates
- Creating a `TotalPrice` column = Quantity × UnitPrice

This significantly improved the quality and consistency of the data.

> **Why this matters:** Clean data allows accurate analysis and modeling. No business insight is reliable without clean input.

---

## 📊 3. Exploratory Data Analysis (EDA)

I conducted a deep dive into the cleaned data to identify trends and patterns.

### 🌍 Country Analysis:
- The United Kingdom dominates the revenue (over 82%)
- Other strong markets include Germany, France, and Ireland

### 📦 Product Analysis:
- Identified top 10 most-purchased and top revenue-generating products
- Found hero products that rank high in both

### 👥 Customer Behavior:
- Analyzed quantity, revenue, and average order value per customer
- Identified high-value customers worth targeting for loyalty programs

### ⏰ Time-Based Trends:
- Sales peak during weekdays and working hours
- Seasonal spikes around holidays

> **Why this matters:** These findings help businesses optimize campaigns, pricing, and inventory.

---

## ⚙️ 4. Feature Engineering

I created new features to capture customer behavior and product performance:

### Customer Features:
- Recency: Days since last purchase
- Frequency: Number of unique transactions
- Monetary: Total spend
- Average Order Value and Items per Order

### Product Features:
- Total units sold
- Total revenue
- Average price
- Popularity score (normalized total quantity sold)

These features were later used for modeling, segmentation, and recommendations.

> **Why this matters:** Rich features unlock deeper insights and smarter predictions.

---

## 🤝 5. Recommendation Systems

I implemented 3 types of recommenders:

### 📄 Content-Based:
- Used TF-IDF on product descriptions
- Found similar products based on text similarity

### 👥 Collaborative Filtering:
- Built a customer-product matrix
- Recommended products based on similar users’ purchase history

### 🔀 Hybrid:
- Blended both systems using a weight parameter `α`

> **Why this matters:** Intelligent product recommendations increase engagement and sales.

---

## 🔍 6. Customer Segmentation

I applied RFM analysis and clustering to group customers.

### RFM (Recency, Frequency, Monetary):
- Scaled features and applied KMeans clustering
- Used the Elbow Method to find optimal cluster count (K=4)

### Segments Identified:
- VIP customers
- Frequent bargain buyers
- Potential loyalists
- At-risk or churned customers

> **Why this matters:** Segmentation supports personalization, retention strategies, and high-ROI marketing.

---

## 🧠 7. Predictive Modeling: Will a Customer Reorder?

I built a binary classification model to predict if a customer would reorder a product.

### Target:
- 1 if a customer purchased the same item more than once, else 0

### Models:
- Logistic Regression (baseline)
- Random Forest (class-balanced)
- XGBoost (best performance)

### Features Used:
- Quantity, UnitPrice, TotalPrice
- RFM values
- Product Popularity
- Country (one-hot encoded)

I evaluated models using precision, recall, and F1 score. XGBoost gave the most consistent results across metrics.

> **Why this matters:** Helps automate remarketing, manage inventory, and retain customers.

---

## 🚀 8. Real-Time Reorder Prediction App

To make this model usable by non-technical users, I built and deployed a Flask web app.

### Key Features:
- Dropdown selection of CustomerID and Product
- Realtime prediction of reorder probability
- User-friendly UI using HTML, CSS, and Select2
- Clean console logs for debug and traceability

> **Why this matters:** This is the final step in making data science impactful — taking it from notebooks to usable applications.

---

## 🧩 Tools & Technologies Used

- **Languages & Libraries:** Python, Pandas, NumPy, Seaborn, Matplotlib, Scikit-learn, XGBoost
- **ML & NLP:** TF-IDF, Cosine Similarity, KMeans, Logistic Regression, Random Forest, XGBoost
- **Web Development:** Flask, HTML, CSS, JavaScript (Select2.js)
- **Deployment:** Flask-Ngrok, Jupyter Notebook
