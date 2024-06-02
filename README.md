# <p align="center">Netflix Shows and Movies Project</p>
# <p align="center">![Pic](https://i.ibb.co/Q81WwRN/92399716.jpg)</p>

[Datasets Used](https://www.kaggle.com/datasets/victorsoeiro/netflix-tv-shows-and-movies?select=titles.csv)

Business Problem: Netflix wants to gather useful insights on their shows and movies for their subscribers through their datasets. The issue is, they are working with too much data (approximately 82k rows of data combined) and are unsure how to effectively analyze and extract meaningful insights from it. They need a robust and scalable data analytics solution to handle the vast amount of data and uncover valuable patterns and trends.



Questions I Wanted To Answer From the Dataset:

## Questions I Wanted To Answer From the Dataset:

## 1. Which movies and shows on Netflix ranked in the top 10 and bottom 10 based on their IMDB scores?
- Top 10 Movies
```mysql
SELECT title, 
type, 
imdb_score
FROM shows_movies.titles
WHERE imdb_score >= 8.0
AND type = 'MOVIE'
ORDER BY imdb_score DESC
LIMIT 10
```
![Q1](https://i.ibb.co/6mQWCw9/Screen-Shot-2023-07-09-at-9-38-11-PM.png)

- Top 10 Shows
```mysql
SELECT title, 
type, 
imdb_score
FROM shows_movies.titles
WHERE imdb_score >= 8.0
AND type = 'SHOW'
ORDER BY imdb_score DESC
LIMIT 10
```
Result: 

![Q2](https://i.ibb.co/QppHsN2/Screen-Shot-2023-07-09-at-9-45-58-PM.png)

- Bottom 10 Movies
```mysql
SELECT title, 
type, 
imdb_score
FROM shows_movies.titles
WHERE type = 'MOVIE'
ORDER BY imdb_score ASC
LIMIT 10
```
Result: 

![Q3](https://i.ibb.co/tMXV1yp/Screen-Shot-2023-07-09-at-9-47-24-PM.png)

- Bottom 10 Shows
```mysql
SELECT title, 
type, 
imdb_score
FROM shows_movies.titles
WHERE type = 'SHOW'
ORDER BY imdb_score ASC
LIMIT 10
```
Result: ![Q4](https://i.ibb.co/Y7Qjvg5/Screen-Shot-2023-07-09-at-9-49-36-PM.png)

## 2. Which genres are the most common? 
- Top 10 most common genres for MOVIES
```mysql
SELECT genres, 
COUNT(*) AS title_count
FROM shows_movies.titles 
WHERE type = 'Movie'
GROUP BY genres
ORDER BY title_count DESC
LIMIT 10;
```
Result:![Q5](https://i.ibb.co/VWrgd8m/Screen-Shot-2023-07-10-at-12-25-40-PM.png)

- Top 10 most common genres for SHOWS
```mysql
SELECT genres, 
COUNT(*) AS title_count
FROM shows_movies.titles 
WHERE type = 'Show'
GROUP BY genres
ORDER BY title_count DESC
LIMIT 10;
```
Result: ![Q6](https://i.ibb.co/P59s4X7/Screen-Shot-2023-07-10-at-12-27-41-PM.png)

- Top 3 most common genres OVERALL
```mysql
SELECT t.genres, 
COUNT(*) AS genre_count
FROM shows_movies.titles AS t
WHERE t.type = 'Movie' or t.type = 'Show'
GROUP BY t.genres
ORDER BY genre_count DESC
LIMIT 3;
```
Result: ![Q7](https://i.ibb.co/qMvMBGf/Screen-Shot-2023-07-10-at-12-30-04-PM.png)

## Conclusion 
By exploring various aspects of the dataset, a comprehensive understanding of Netflix's content landscape was gained. The analysis revealed the top 10 and bottom 10 movies and shows based on their IMDB scores, which highlighted the titles that garnered high praise and those that received lower ratings. This information can assist viewers in making informed choices and highlight areas for potential improvement in content quality. The examination of movies and shows distributed across different decades showed significant shifts in content availability over time. Notably, the dataset showcased a substantial increase in offerings from the 2000s onwards, emphasizing Netflix's commitment to featuring newer content that resonates with current trends and audience preferences.

