# Ngo-Impact-analysis
The goal of the project is to gain insights into the effectiveness of assignments (projects) and the contributions from donors to maximize impact and make informed decisions about where to allocate resources.
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
