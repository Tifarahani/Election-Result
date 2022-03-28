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


