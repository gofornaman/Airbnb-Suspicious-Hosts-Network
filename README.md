# Airbnb-Suspicious-Hosts-Network
Identify networks of suspicious hosts with duplicate/ fake listings connected by fake reviewers using network analysis

## Problem statement
Hosts on Airbnb create fake listings for numerous reasons such as

- To by-pass the 30/90 nights limit in countries such as Amsterdam or London
- Defraud the guests by using "bait and switch" method which involves double booking and last minute rescheduling to another listing
- If a listing has multiple negative reviews, it is a better option for the hosts to create another listing with some of the details changed
- Create multiple listings with fake reviewers leaving positive reviews to boost the ranking of the host

## Approach
The core assumption here is the hosts uses fake reviewers to leave positive reviews on his/her listings. This way, the host can quickly get some credibility around the new listing. Following are the steps involved in identifying these suspicious hosts -

Step 1: Fetch the "listings" and "reviews" dataset for Amsterdam and London until July 2021 from "Inside Airbnb"
Step 2: Use NetworkX to create a bi-partite graph that connects host_id and reviewer_id using listing_id as a bridge
Step 3: Once "related" hosts are identified, pick the reviews - compute polarity score for each review and generate different word clouds for positive and negative reviews. We are trying to understand if the negative reviews contain words like "fraud" or "scam" which could be posted by a genuine reviewer or contains repetitive positive words (across different listings) which could be posted by a suspected fake reviewer.
Step 4: Fetch the suspected hosts and listings, and run Levenshtein distance or any other similarity measure on features such as names, address, phone number, location, listing pictures etc.
Step 5: Finally, we can infer with a certain confidence that X hosts are actually fake or running a scam listing operation. We can also compute the revenue lost by genuine customers staying at the listing and having a bad experience.

![Example Scenario](https://github.com/gofornaman/Airbnb-Suspicious-Hosts-Network/blob/main/img/example_scenario.png)
---

* Link to the presentation - http://tiny.cc/rp2iuz 
* Link to the notebook - http://tiny.cc/0q2iuz



-----------
