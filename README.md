# FMWC
Financial Modeling World Cup

![alt text](https://github.com/blanchardmike/FMWC/blob/main/Resources/FMWC_Instructions.png)


![alt text](https://github.com/blanchardmike/FMWC/blob/main/Resources/FMWC_Rules.png)

First round, easy enough. The question is to evaluate the points given by the item obtained by the "roll", which is how many times the number, (Red cell 35 in Example1) "spins" through top to bottom, starting at top left yellow cell, Cherries, in the Reel Strip/Refernce chart. 

Board                                                    |Reference                                   |Reward
:-------------------------------------------------------:|:-----------------------------------------:|:------------------------------------------------------:
![](https://github.com/blanchardmike/FMWC/blob/main/Resources/FMWC_Q1.png?raw=true)|![](https://github.com/blanchardmike/FMWC/blob/main/Resources/FMWC_Reel.png)|![](https://github.com/blanchardmike/FMWC/blob/main/Resources/FMWC_Reward.png)

The roll starts at top left Cherries, we OFFSET that reference cell by the remainder of Roll/19, using MOD(X, 19). Then we XLOOKUP the result, bell, highlighted Green, to get 30 points. 

Knowing the Reward table will be referenced frequently, 'symbol' and 'amount' named ranges were given to the Item and Base Pts columns of the Rewards table.

The 'TRUE' column is referencing the answers table, correct or not. 

![](https://github.com/blanchardmike/FMWC/blob/main/Resources/FMWC_Q1_formula.png)

Second round, interesting change. Same idea as above.

![](https://github.com/blanchardmike/FMWC/blob/main/Resources/FMWC_Q2.png)

We have to make one important change, adding MOD(G60 + H60) for turn 2 and MOD(G60 + H60 + I60) for turn 3, as every roll starts from the position of the last. 

![](https://github.com/blanchardmike/FMWC/blob/main/Resources/FMWC_Q2_formula.png)


![](https://github.com/blanchardmike/FMWC/blob/main/Resources/FMWC_Q3.png)

Starts with a simple XLOOKUP as before.

![](https://github.com/blanchardmike/FMWC/blob/main/Resources/FMWC_Q3_lookup.png)

Wanting to list the unique values, but UNIQUE() only works vertically, so had to TRANSPOSE() the values to count uniques. Since I wanted to keep them all on the same row for future use, TRANSPOSE() them back. 

![](https://github.com/blanchardmike/FMWC/blob/main/Resources/FMWC_Q3_transpose.png)

we can count the occurences in this new field with COUNTIF()

![](https://github.com/blanchardmike/FMWC/blob/main/Resources/FMWC_Q3_countif.png)

Then square the count by the value, satisfying the rule duplicates are multiplied together.

![](https://github.com/blanchardmike/FMWC/blob/main/Resources/FMWC_Q3_square.png)

This results in errors, so SUM() function will not work. we use AGGREGATE() to ignore error cell and choose the 5 column field. 

![](https://github.com/blanchardmike/FMWC/blob/main/Resources/FMWC_Q3_aggregate.png)
