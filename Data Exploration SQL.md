# PortfolioProjects
# Data Exploration SQL
## Project Goal
Explore the Sakila database to derive insights about movie rentals, customers, and inventory using SQL queries.
## Sakila Database Overview
The Sakila database consists of several tables, including film, customer, rental, inventory,payment among others, which contain information about films, customers, rentals, and inventory.
## Exploration Steps
1. Connecting to the Sakila Database:
Connect to the Sakila database in MySQL Workbench to start querying the data.
2. Basic Queries:
   . Total Number of Films: Count the total number of films available.
    SELECT COUNT(*) AS total_films
FROM film;
   . payment date for each customer whose name begins with "A"

   select
customer.customer_id,
first_name,
last_name,
email,
amount,
payment_date


 from customer
 inner join payment on payment.customer_id = customer.customer_id
 
 where last_name like 'A%'
 order by customer.customer_id asc;
 
 


 
  . Top Categories by Film Count: Determine the most popular film categories.
  SELECT film_id, customer_id
FROM film_category 
JOIN customer ON film_category.category_id = customer_id
ORDER BY film_id DESC
LIMIT 5;

  . Identify the top 10 customers who have rented the most films.

SELECT c.customer_id, c.first_name, c.last_name, COUNT(r.rental_id) AS rental_count
FROM customer c
JOIN rental r ON c.customer_id = r.customer_id
GROUP BY c.customer_id, c.first_name, c.last_name
ORDER BY rental_count DESC
LIMIT 10;

   . Analyze rental trends by month.

SELECT MONTH(rental_date) AS rental_month, COUNT(rental_id) AS rentals_count
FROM rental
GROUP BY rental_month;

   . Determine the average rental duration.
SELECT AVG(return_date - rental_date) AS avg_rental_duration
FROM rental;

