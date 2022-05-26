# MarkstorySQL
## Tasks that we have to face in order to be able to answer the questions below
## Key Questions and Objectives

### The Rockbuster Stealth Management Board has asked a series of business questions and
### they expect data-driven answers that they can use for their 2020 company strategy. Here are
### the main questions they’d like to answer:

#### ● Which movies contributed the most/least to revenue gain?
#### ● What was the average rental duration for all videos?
#### ● Which countries are Rockbuster customers based in?
#### ● Where are customers with a high lifetime value based?
#### ● Do sales figures vary between geographic regions?

## Basic SQL querries 
#### SELECT rental_duration AS "rented for (in days)", COUNT(*) AS "number of films"
#### FROM  film
#### GROUP BY 1
#### ORDER BY 2

## Basic SQL querries
#### SELECT film_id,
#### title
#### FROM film
 ## check the result https://drive.google.com/file/d/1IH7oYScP49Qlp8dLoMpE0qwd6oK9V4Kg/view?usp=sharing

## Basic SQL querries
#### SELECT title,
#### release_year,
#### rental_rate
#### FROM film
#### ORDER BY title,
#### release_year,
#### rental_rate DESC
## check the result https://drive.google.com/file/d/105SnB7rCwEudOttbFaOoaZRq_rCudtiK/view?usp=sharing

## Bit more advanced querries
#### SELECT film_id,
#### title,
#### description
#### FROM film
#### WHERE length> 120
#### AND rental_rate >2.99
## check the result https://drive.google.com/file/d/1Gzd7TxxZ_F3CQQOxMhxt0ld6KqmGwoSk/view?usp=sharing

## Bit more advanced querries
#### SELECT rating
#### COUNT(film_id) AS count_of_movies,
#### AVG(rental_rate) AS average_rental_rate,
#### MIN(rental_duration) AS min_rental_duration,
#### MAX(rental_duration) AS max_rental_duration
#### FROM film
#### WHERE rating='PG' OR rating='G'
#### GROUP BY rating
## check the result [https://drive.google.com/file/d/1SqFsP3yH_6nPhU7nIKJtWkLDNcYmxGNV/view?usp=sharing]

## SQL Joints
#### SELECT D.country,
#### COUNT(customer_id) AS customer_count
#### FROM customer A
#### INNER JOIN address B ON A. address_id=B. address_id
#### INNER JOIN city C ON B. city_id= C. city_id
#### INNER JOIN country D ON C. country_id= D. county_id
#### GROUP BY country
#### ORDER BY COUNT(customer_id) DESC
#### LIMIT 10
## check the result https://drive.google.com/file/d/1iUiYlLmVUQunLres_ZqhUXidYBBrlHxX/view?usp=sharing

## Bit more advanced Joints
#### SELECT country.country,
#### COUNT (DISTINCT customer.customer_id) AS all_customer_count,
#### COUNT (DISTINCT country.country) AS top_costumer_count
#### FROM
#### (SELECT
#### A.customer_ID,
#### B.first_name,
#### B.last_name,
#### D.city,
#### E.country,
#### SUM (amount) AS total_amount_paid
#### FROM payment A
#### INNER JOIN customer B ON A.customer_id = B.customer_id
#### INNER JOIN address C ON B.address_id = C.address_id
#### INNER JOIN city D ON C.city_id = D.city_id
#### INNER JOIN country E ON D.country_id = E.country_id
#### WHERE E.country IN
#### ('India',
#### ‘China’,
#### 'United States’,
#### 'Japan',
#### 'Mexico',
#### 'Brazil',
#### 'Russian Federation’,
#### 'Philippines',
#### 'Turkey',
#### ‘Indonesia’
#### )
#### AND D.city in
#### (
#### ‘Aurora’,
#### 'Atlixco',
#### 'Xintai',
#### 'Adoni',
#### 'Dhule (Dhulia)',
#### 'Kurashiki',
#### 'Pingxiang',
#### 'Sivas',
#### 'Celaya',
#### 'So Leopoldo'
#### )
#### GROUP BY
#### A.customer_ID,
#### B.first_name,
#### B.last_name,
#### D.city,
#### E.country
#### ORDER BY total_amount_paid DESC
#### LIMIT 5 ) AS top_S_customers
#### LEFT JOIN custonpr ON customer.customer_id = customer.customer_id
#### LEFT JOIN address ON customer.address_id = address.address_id
#### LEFT JOIN city ON address.city_id = city.city_id
#### LEFT JOIN country ON city.country_id = country.country_id
#### GROUP BY country.country
#### ORDER BY COUNT (country.country) DESC
### check the result https://drive.google.com/file/d/1uLrcFcDYGOMquMMm6uog5sIn9_noq3k8/view?usp=sharing
# Link to My presentation
## https://coach-courses-us.s3.amazonaws.com/exercises/1054/46313/f475c86809fac07a65d6aa198ae944f9/bussines-analysis.pdf
