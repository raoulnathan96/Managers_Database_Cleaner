# Managers_Database_Cleaner
** DESCRIPTION FOR "CEO_CFO_Market.ipynb" **
I used pandas and fuzzywuzzy to segregrate CEOs and CFOs from a list of managers at different positions
The objective is to segregate CEOs and CFOs from all the managers in the list 'Total_Managers_pos.csv'
The CSV contains a column 'positions' which contains the designation of the managers
The easiest case is when the title is simply 'CEO' or 'Chief Executive Officer' (similar for CFO) and this is filtered out easily in the initial stages
To remove problems like unnecessary capitalization, double spaces, etc. I filtered the whole column with strip() and capitalize() to ensure uniformity
To identify simple spelling and punctuation errors in these cases, I used the fuzzywuzzy function
Fuzzywuzzy does not eliminate repititions, so I created a custom function to take all its output values, eliminate reps. and extend them into a list
In stage two, I successfully found the basic spelling errors eg. 'Cheif' instead of 'Chief', 'Eexcutive' instead of 'Executive'
Now that the single designation cases were handled, I moved to the multiple designation cases eg. CEO, President and Director
I used the contains() function of pandas to filter out the multiple title cases and analyze the remaining ones for spelling errors
In stage 3 of this analysis, I had to demarcate the managers who were not strictly CEOs and CFOs, but held the title in an interim or deputy capacity eg. Acting CFO
After a lot of fuzzywuzzy iterations with both cases, I managed to weed out all the spelling mistakes and now could mark the designations

** DESCRIPTION FOR "Final_Managers_Script.ipynb" **
In the code for creating a column with index 0 = False for being CEO or CFO and index 1 = True
Repeated the initial cleanup of formatting errors like in Line 7 of this README
Defined custom function to assign the binary indices based on all my findings and spelling mistakes
Tried to use a loop function on the lists I acquired earlier, but found that looping over columns in pandas is particularly difficult and went manual instead
Did the indexing for the Interim or Acting designations first, so I could put the condition Index = 0 if the Interim Index = 1
This was particularly helpful as someone could be an 'Executive Officer' but that did not make them a CEO and the reverse method wouldn't work

** CONCLUSION **
Tried my best to describe my process flow in the most basic way possible, please contact me to understand any part of this better
If somebody has any suggestions on how I could have avoided the heavy manual programming in phase 2, please let me know!
