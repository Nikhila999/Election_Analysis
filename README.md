# Election_Analysis

## Overview of Election Audit
A Colorado Board of Elections employee has given the following tasks to complete the election audit of a recent local congressional election.
    - Calculate the total number of votes cast.
    - Get a complete list of candidates who received votes.
    - Calculate the total number of votes each candidate received.
    - Calculate the percentage of votes each candidate won.
    - Determine the winner of the election based on popular vote.

## Challenge Overview
After reviewing the above information, the election commision has requested for more information to complete the audit.
    - The voter turnout for each county
    - The percentage of votes from each county out of the total count
    - The county with the highest turnout

## Resources
- Data Source: election_results.csv
- Software: Python 3.7.3, Visual Studio Code, 1.59.1

## Election-Audit Results

1. How many votes were cast in the congressional election?
    - There were 369,711 votes cast in the election. These are the number of ballot IDs in the dataset we received.
    
2. Provide a breakdown of the number of votes and the percentage of total votes for each county in the precinct
    - The number of votes and percentage of total votes received by each county is
        * Jefferson county has received 38,855 votes, 10.5% of the total votes.
        * Denver county has received 306,055 votes, 82.8% of the total votes.
        * Arapahoe county has received 24,801 votes, 6.7% of the toal votes.
    - To calculate the number and percentage of votes by county, we use below code.
    
    Code:      
    
          `for c_name in county_names:
            c_votes = county_votes[c_name]
            c_vote_percentage = float(c_votes)/float(total_votes) * 100`


3. Which county had the largest number of votes?
    -  Denver county has the largest number of votes.
    - We are using a conditional statement to check the largest turnout county, going through all the records (using for loop)
    
    Code:
        
          `if (c_votes > largestturnout_votes):   
           largestturnout_county = c_name
            largestturnout_votes = c_votes`

4. Provide a breakdown of the number of votes and the percentage of the total votes each candidate received.

    - The candidate results are:
        * Charles Casper Stockham received 23.0% of the vote and 85,213 number of votes.
        * Diana DeGette received 73.8% of the vote and 272,892 number of votes.
        * Raymon Anthony Doane received 3.1% of the vote and 11,606 number of votes.
    - We are using below code to collect the candidates name from election_results.csv file by looping over all the rows and adding a candidate name to the list if the name is not on it.
    
    Code:
    
            `if candidate_name not in candidate_options:
                # Add the candidate name to the candidate list.
                candidate_options.append(candidate_name)`        
        
5. Which candidate won the election, what was their vote count, and what was their percentage of the total votes?
    - Winner of the congressional election is Diana DeGette, with 272,892 votes, that is 73.8% of the total votes.
    - We are using a conditional statement to check the highest number of votes and percentages for a candidate going through all the records (using for loop) 
    
    Code:
    
            `if (votes > winning_count) and (vote_percentage > winning_percentage):
                winning_count = votes
                winning_candidate = candidate_name
                winning_percentage = vote_percentage`

## Election-Audit Summary

The election-audit python code we built can be used for auditing any election with few minor changes.
1. Adding type of election (like general election, municipal election) column to the dataset would give our code the ability to expand into various types of elections. 
2. Depending on the type of election, adding a area/state column would help in determining the winning candidate at area/state level.


