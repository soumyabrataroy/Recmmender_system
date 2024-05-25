# Recommender_system

This Python code implements a customer user based and item based collaborative filtering recommendation system for an e-commerce website. It uses data from a CSV file containing customer IDs, product IDs (StockCode), and quantities purchased (Quantity).

1. **Data Loading and Cleaning**:

- The code first downloads a ZIP file containing the data and extracts its contents.
- It then reads the CSV file into a Pandas DataFrame and removes any records with negative values in the Quantity or UnitPrice columns.
- Records with missing customer IDs are also dropped.

2. **Customer-Item Matrix**:

- A customer-item matrix is constructed using the `pivot_table` function in Pandas. This matrix has customer IDs as the index and product IDs as the columns.
- The values in the matrix represent the quantity of each product purchased by each customer.
- The code then converts all values above 1 to 1 and replaces missing values (NaNs) with 0.

3. **User-to-User Similarity Matrix**:

- The code uses the `cosine_similarity` function from scikit-learn to compute the pairwise cosine similarities between customers based on their purchase history.
- The resulting matrix is a square matrix with customer IDs as both the index and columns.

4. **Finding Similar Customers and Recommendations**:

- The code defines a function `get_items_to_recommend_cust` that takes a customer ID as input and returns a list of recommended products.
- This function first identifies the most similar customer based on the user-to-user similarity matrix.
- It then finds the items purchased by the most similar customer but not by the input customer.
- Finally, it retrieves the descriptions of these recommended products from the original data frame.

5. **Item-Based Collaborative Filtering**:

- The code also constructs an item-item similarity matrix using the `cosine_similarity` function. This matrix has product IDs as both the index and columns.
- A function `get_top_similar_items` is defined to return the top 10 most similar products for a given product ID.

Overall, this code demonstrates how to build a basic collaborative filtering recommendation system using Python and scikit-learn. The system can be further improved by incorporating additional data, such as product ratings or reviews, and by using more sophisticated recommendation algorithms.
