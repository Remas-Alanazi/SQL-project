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
# 5. Locations with the most entertainment venues
```sql
SELECT name, location, genre FROM ksa
WHERE best_comment IS NULL
ORDER BY name ASC;
```
### This query lists locations in the ksa table with the highest number of entertainment venues, helping to understand where these businesses are most concentrated.
![image](https://github.com/user-attachments/assets/dc1e88d7-a4b8-4071-ae85-6c7143009ca2)

# 6. Highest rated venues per genre
```sql
use movies;
SELECT genre, name, rating
FROM ksa
WHERE rating = (SELECT MAX(rating) FROM ksa AS e WHERE e.genre = ksa.genre);
```
### This query finds the highest-rated venue for each genre in the ksa table, showcasing the best performers in each category.
![image](https://github.com/user-attachments/assets/84748388-3157-495f-bbb2-ce026e3a82b4)

# 7. Percentage of venues with a rating of 5
```sql
SELECT COUNT(*) * 100.0 / (SELECT COUNT(*) FROM ksa) AS percentage_five_star
FROM ksa
WHERE rating = 5;
```
### This query calculates the percentage of venues in the ksa table that have a perfect 5-star rating, giving insight into overall customer satisfaction.
![image](https://github.com/user-attachments/assets/cfedb8ee-3ec5-4072-b5b9-c50d05a0fd7a)

# 8. Locations with the highest average rating
```sql
SELECT location, AVG(rating) AS avg_rating
FROM ksa
GROUP BY location
ORDER BY avg_rating DESC
LIMIT 5;
```
### This query lists the top 5 locations with the highest average ratings in the ksa table, highlighting areas with the best-rated entertainment options.
![image](https://github.com/user-attachments/assets/27b9e79b-d12e-44a4-b0ec-27fc99175b08)
# 9. Most common words in best comments
```sql
SELECT word, COUNT(*) AS word_count
FROM (
    SELECT SUBSTRING_INDEX(SUBSTRING_INDEX(best_comment, ' ', n), ' ', -1) AS word
    FROM ksa
    JOIN (SELECT 1 n UNION SELECT 2 UNION SELECT 3 UNION SELECT 4 UNION SELECT 5) numbers
    ON CHAR_LENGTH(best_comment) - CHAR_LENGTH(REPLACE(best_comment, ' ', '')) >= n - 1
) words
WHERE word IS NOT NULL
GROUP BY word
ORDER BY word_count DESC
LIMIT 20;
```
### This query extracts and counts the most common words used in customer reviews from the ksa table, helping to understand common themes in feedback.
![image](https://github.com/user-attachments/assets/c4412eb5-88ab-43a7-a682-25f1cd3517c6)

# 10. Finding venues with the lowest ratings
``` sql
SELECT name, location, rating FROM ksa
ORDER BY rating ASC
LIMIT
```
### This query retrieves the bottom 10 entertainment venues with the lowest ratings from the ksa table, helping identify locations that might need improvement.

![image](https://github.com/user-attachments/assets/e1e53762-3adb-470d-b73c-fc315c514325)





