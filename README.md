# SQL-project
## This project demonstrates how to work with a dataset containing information about entertainment venues, including cinemas and theaters. We will use MySQL to analyze the dataset, covering data cleaning, transformation, and insightful queries.

# 1.Finding venues with the most reviews
```sql
use movies;
SELECT name, review_count FROM ksa
ORDER BY review_count DESC
LIMIT 10;
```
### This query retrieves the top 10 entertainment venues with the most reviews from the ksa table, helping identify the most popular locations.
![image](https://github.com/user-attachments/assets/f5de8df7-b0dd-4819-beb6-3d76dfe864ed)

# 2. Average rating per location
```sql
SELECT location, AVG(rating) AS avg_rating
FROM ksa
GROUP BY location
ORDER BY avg_rating DESC;
```
### This query calculates the average rating of venues in each location within the ksa table, allowing us to compare customer satisfaction across different areas.
![image](https://github.com/user-attachments/assets/8790f023-ed28-47bc-93e5-75d10da1d883)

# 3. Total number of venues per genre
```sql
SELECT genre, COUNT(*) AS total_venues
FROM ksa
GROUP BY genre;
```
### This query finds the number of venues for each type of entertainment in the ksa table, giving insights into which types are most common.
![image](https://github.com/user-attachments/assets/be9aa7a2-6798-41ee-837b-db170fb2a103)

# 4. Most frequently reviewed genres
```sql
SELECT genre, SUM(review_count) AS total_reviews
FROM ksa
GROUP BY genre
ORDER BY total_reviews DESC;
```
### This query identifies the entertainment genres in the ksa table with the highest total number of reviews, indicating which types of venues attract the most customer engagement.
![image](https://github.com/user-attachments/assets/e32b8dc5-6490-4a63-a1a3-545fe69150d4)


