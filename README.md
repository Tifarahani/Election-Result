## Election_Analysis
# 1.Overview of Election Audit
A Colorado Board of Elections employee has given you the following task to complete the election audit of a recent local congressional election.



## Resources:
* Data Source: Election_result.csv
* Software: Python: 3.9.7
* Visual Studio Code

## Summary
* There were 369,711 votes cast in the election
The Analysis of the election shows that:
* Candididates were:
 * Charles Casper Stockham
 * Diana DeGette
 * Raymon Anthony Doane: 3.1% (11,606)
 
* County Votes were:
  * Jefferson: 10.5% (38,855)
  * Denver: 82.8% (306,055)
  * Arapahoe: 6.7% (24,801)
-------------------------
- Largest County Turnout: Denver
- Winning Count Vote: 306,055
- Winning Count Percentage: 82.8%


* The Candidate result were:
  * Charles Casper Stockham: recieved "23.0%" of the votes and "85,213" number of votes.
  * Diana DeGette recieved "73.8% " of the votes and "272,892" number of votes.
  * Raymon Anthony Doane recieved "3.1%" of the votes and "11,606" number of votes.
### Election Results:
*  The winner of the election was:
   * Candidate "Diana DeGette", who recieved "73.8%" of the votes and "272,892" number of the votes
   
## Challenge Overview
**1)** Calculate the total number of votes cast

**2)** Get a complete list of candidate who recieved votes.

**3)** Calculate the total number of votes each candidate recieved.

**4)** Calculate the percentage of votes each candidate won.

**5)** Determine the winner of the election based on popular vote.

![Text_file](https://github.com/Tifarahani/Election-Result/blob/main/Resources/Text_file.png)

## Challenge Summary
- This programm is written to analyze the election_results.csv file by going through each row and reading the data in the second and third columns, 'County' and 'Candidate', in order to calculate and print the results. There are many different ways in which this code can be changed and used with any election results.

1) Determining which additional columns to read data from in order to calculate and print more results. This is useful for files containing more information, such as the type of ballot or the date that the vote was cast.no matter the number of candidates or counties, the script used to perform the Election Audit can be a valuable resourse for the board.Similarly, if this were a federal election, we could use the same script and change the county to states.

2) By importing other dependency such as datetime we could perform real-time results for election in progress. datetime dependency will capture exact time when the analysis is executed.



# -*- coding: UTF-8 -*-
"""PyPoll Homework Challenge Solution."""

# Add our dependencies.
import csv
import os
from pydoc import describe

# Add a variable to load a file from a path.
file_to_load = os.path.join(".." ,"Resources", "election_results.csv")
# Add a variable to save the file to a path.
file_to_save = os.path.join("..","Resources", "election_analysis.txt")


# Initialize a total vote counter.
total_votes = 0

# Candidate Options and candidate votes.
candidate_options = []
candidate_votes = {}

## 1: Create a county list and county votes dictionary.
county_list = []
county_votes = {}

# Track the winning candidate, vote count and percentage
winning_candidate = ""
winning_count = 0
winning_county = 0
winning_percentage = 0
winning_c_percentage = 0

# 2: Track the largest county and county voter turnout.
largest_turnout_county = ""
largest_turn_count = 0

# Read the csv and convert it into a list of dictionaries
with open(file_to_load) as election_data:
    reader = csv.reader(election_data)

    # Read the header
    header = next(reader)

    # For each row in the CSV file.
    for row in reader:

        # Add to the total vote count
        total_votes = total_votes + 1

        # Get the candidate name and county name from rows.
        candidate_name = row[2]

        # 3: Extract the county name from each row.
        county_name = row[1]


        # If the candidate does not match any existing candidate add it to
        # the candidate list
        if candidate_name not in candidate_options:

            # Add the candidate name to the candidate list.
            candidate_options.append(candidate_name)

            # And begin tracking that candidate's voter count.
            candidate_votes[candidate_name] = 0

        # Add a vote to that candidate's count
        candidate_votes[candidate_name] += 1

        # 4a: Write a decision statement that checks that the
        # county does not match any existing county in the county list.
        if county_name not in county_list:  

            # 4b: Add the existing county to the list of counties.
            county_list.append(county_name)

            # 4c: Begin tracking the county's vote count.
            county_votes[county_name] = 0

        # 5: Add a vote to that county's vote count.
        county_votes[county_name] += 1


# Save the results to our text file.
with open(file_to_save, "w") as txt_file:

    # Print the final vote count (to terminal)
    election_results = (
        f"Election Results\n"
        f"-------------------------\n"
        f"Total Votes: {total_votes:,}\n"
        f"-------------------------\n\n"
        f"County Votes:\n"
        f"-------------------------\n")
    print(election_results, end="")

    txt_file.write(election_results)

    # 6a: Write a repetition statement to get the county from the county dictionary.
    for county_name in county_votes:
        # 6b: Retrieve the county vote count.
        county = county_votes.get(county_name)

        # 6c: Calculate the percent of total votes for the county.
        county_percentage = float(county) / float(total_votes) * 100
        county_results = (
            f"{county_name}: {county_percentage:.1f}% ({county:,})\n")

         # 6d: Print the county results to the terminal.
        print(county_results, end="")
         # 6e: Save the county votes to a text file.
        txt_file.write(county_results)
         # 6f: Write a decision statement to determine the winning county and get its vote count.
        if (county > winning_county) and (county_percentage > winning_c_percentage):
            winning_county = county
            winning_c_candidate = county_name
            winning_c_percentage = county_percentage

    # 7: Print the county with the largest turnout to the terminal.
    winning_county_summary = (
        f"-------------------------\n"
        f"Largest County Turnout: {winning_c_candidate}\n"
        f"Winning Count Vote: {winning_county:,}\n"
        f"Winning Count Percentage: {winning_c_percentage:.1f}%\n"
        f"-------------------------\n\n"
        f"Candidate Percentage of Votes:\n"
        f"-------------------------\n")
    print(winning_county_summary)

    # 8: Save the county with the largest turnout to a text file.
    txt_file.write(winning_county_summary)

    # Save the final candidate vote count to the text file.
    for candidate_name in candidate_votes:

        # Retrieve vote count and percentage
        votes = candidate_votes.get(candidate_name)
        vote_percentage = float(votes) / float(total_votes) * 100
        candidate_results = (
            f"{candidate_name}: {vote_percentage:.1f}% ({votes:,})\n")

        # Print each candidate's voter count and percentage to the
        # terminal.
        print(candidate_results)
        #  Save the candidate results to our text file.
        txt_file.write(candidate_results)

        # Determine winning vote count, winning percentage, and candidate.
        if (votes > winning_count) and (vote_percentage > winning_percentage):
            winning_count = votes
            winning_candidate = candidate_name
            winning_percentage = vote_percentage

    # Print the winning candidate (to terminal)
    winning_candidate_summary = (
        f"\n-------------------------\n"
        f"Winner: {winning_candidate}\n"
        f"Winning Vote Count: {winning_count:,}\n"
        f"Winning Percentage: {winning_percentage:.1f}%\n"
        f"-------------------------\n")
    print(winning_candidate_summary)

    # Save the winning candidate's name to the text file
    txt_file.write(winning_candidate_summary)


