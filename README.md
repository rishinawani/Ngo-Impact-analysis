# Ngo-Impact-analysis
The goal of the project is to gain insights into the effectiveness of assignments (projects) and the contributions from donors to maximize impact and make informed decisions about where to allocate resources.

![NGO Logo](https://github.com/rishinawani/Ngo-Impact-analysis/blob/main/ngo_project_image.jpg)

## Overview
GoodThought NGO conducts various assignments aimed at uplifting underprivileged communities. These assignments are data-rich and can be evaluated based on:
### Assignments:
The name, region, duration, and the calculated impact score of each project.
### Donations:
Financial records tied to specific assignments, allowing analysis of funding trends.
### Donors:
The types and identities of donors, helping identify which types of donors contribute most to which projects or regions.
## Dataset Overview
### 1.Assignments Table:
#### Contains information about the specific projects or assignments, such as:
##### >Assignment Name
##### >Geographical Region
##### >Budget
##### >Impact Score
##### >Start and End Dates
### 2.Donations Table:
#### Tracks donations linked to specific assignments:
##### >Donation ID
##### >Assignment ID (to link to specific assignments)
##### >Donor ID (to identify the donor)
##### >Donation Amount
### 3.Donors Table
#### Information about the donors, including:
##### >Donor ID (to match donations with donor)
##### >Donor Type (e.g., individual, corporation, etc.)
## Queries
### 1.Highest Donation Assignments Query:
###### SELECT a.assignment_name, a.region, r.donor_type, 
###### ROUND(SUM(d.amount), 2) AS rounded_total_donation_amount
 ###### FROM donations d 
 ###### JOIN assignments a ON d.assignment_id = a.assignment_id
 ###### JOIN donors r ON d.donor_id = r.donor_id
 ###### GROUP BY a.assignment_name, a.region, r.donor_type
 ###### ORDER BY rounded_total_donation_amount DESC
 ###### LIMIT 5;
### 2.Top Regional Impact Assignments Query:
 ###### WITH assign_count AS (
  ######  SELECT assignment_id, COUNT(donation_id) AS num_total_donations
   ######    FROM donations
   ######   GROUP BY assignment_id
 ###### ),
 ###### ranked_assign AS (
   ######   SELECT a.assignment_name, a.region, a.impact_score, ac.num_total_donations,
   ######        ROW_NUMBER() OVER (PARTITION BY a.region ORDER BY a.impact_score DESC) AS rank_in_region
 ######     FROM assignments a
  ######    JOIN assign_count ac ON a.assignment_id = ac.assignment_id
  ######    WHERE ac.num_total_donations > 0		
 ###### )
 ###### SELECT assignment_name, region, impact_score, num_total_donations
 ###### FROM ranked_assign
 ###### WHERE rank_in_region = 1
 ###### ORDER BY region ASC;
