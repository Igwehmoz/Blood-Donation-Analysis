# Blood-Donation-Analysis
select * from donation_data;

select * from donor_data;
--TASKS

-- How much is the total donation?
SELECT sum(donation) as Total_donation
FROM donation_data;

-- What is the total donation by gender?
SELECT gender, Sum(donation) as Total_donation
FROM donation_data
GROUP BY gender;

-- Show the total donation and number of donations  by gender
SELECT gender, SUM(donation) AS Total_donation, COUNT(donation) AS Number_of_donation
FROM donation_data
GROUP BY gender;

-- Total donation made by frequency of donation
SELECT donor_data.donation_frequency, SUM(donation_data.donation) AS Total_donation
FROM donation_data
INNER JOIN donor_data
ON donation_data.id = donor_data.id
GROUP BY donor_data.donation_frequency;

-- Total donation and number of donation by Job field
SELECT job_field, COUNT(job_field) AS Number_of_donation, SUM(donation) AS Total_donation
FROM donation_data
GROUP BY job_field;

-- Total donation and number of donations above $200
SELECT COUNT(donation) AS Number_of_donation,  SUM(donation) AS Total_donation
FROM donation_data
WHERE donation > 200
--GROUP BY donation;
 
-- Total donation and number of donations below $200
SELECT COUNT(donation) AS Number_of_donation,  SUM(donation) AS Total_donation
FROM donation_data
WHERE donation < 200
--GROUP BY donation;

-- Which top 10 states contributes the highest donations
SELECT state, SUM(donation) AS Total_donation
FROM donation_data
GROUP BY state 
ORDER BY SUM(donation) DESC
LIMIT 10;

-- Which top 10 states contributes the least donations
SELECT state, SUM(donation) AS Total_donation
FROM donation_data
GROUP BY state 
ORDER BY SUM(donation) ASC
LIMIT 10;

-- What are the top 10 cars driven by the highest  donors
SELECT car, COUNT(donation_frequency) AS highest_donor
FROM donor_data
GROUP BY car
ORDER BY COUNT(donation_frequency) DESC
LIMIT 10;
