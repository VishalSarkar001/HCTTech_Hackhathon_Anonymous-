Project Overview
This project automates the data journey for a retail supermarket. It takes raw, messy sales data, cleans it, calculates loyalty rewards, and automatically identifies which customers are "High Value" and which are "At Risk".
The 5-Step Workflow
This project follows a strict 5-step execution plan:
Step 1: Data Collection (Simulation)
We utilize Generative AI (LLMs) to create realistic retail datasets.
Generated Files: stores.csv, products.csv, customer_details.csv, store_sales.csv.
Anomalies: To test our system, we intentionally injected errors (e.g., negative prices, missing Customer IDs) into the source data.
Step 2: Data Loading
The system reads the raw CSV files using Python (Pandas).
It establishes a connection to a local SQLite Database (retail.db) to prepare for storage.
Step 3: Good vs. Bad Data Segregation
We implement a Quality Gatekeeper that validates every single row before processing.
Good Data: Valid records are loaded into the main database tables for processing.
Bad Data: Records with errors (e.g., invalid email, negative transaction amount) are rejected and saved to a separate file rejected_records.csv for analysis.
Step 4: Loyalty Bonus Assignment
For all the Good Data, the system calculates rewards:

It applies promotion rules to calculate points for the current transaction.

It updates the total_loyalty_points balance in the customer_details table.

Step 5: Analysis & File Generation
The system runs a final analysis on the aggregated sales data to generate two specific reports:

High Spenders: Identifies the Top 10% of customers by total money spent. Saved as high_spenders.csv.

At-Risk Customers: Identifies customers with points who haven't shopped in over 30 days. Saved as at_risk_customers.csv.
