# FMWC
Financial Modeling World Cup

![alt text](https://github.com/blanchardmike/FMWC/blob/main/Resources/FMWC_Instructions.png)


![alt text](https://github.com/blanchardmike/FMWC/blob/main/Resources/FMWC_Rules.png)

First round, easy enough. The question is to evaluate the points given by the item obtained by the "roll", which is how many times the number, (Red cell 35 in Example1) "spins" through top to bottom, starting at top left yellow cell "Cherries" in the Reel Strip/Refernce chart. 

Board                                                    |Reference                                   |Reward
:-------------------------------------------------------:|:-----------------------------------------:|:------------------------------------------------------:
![](https://github.com/blanchardmike/FMWC/blob/main/Resources/FMWC_Q1.png?raw=true)|![](https://github.com/blanchardmike/FMWC/blob/main/Resources/FMWC_Reel.png)|![](https://github.com/blanchardmike/FMWC/blob/main/Resources/FMWC_Reward.png)

The roll starts at top left Cherries, we OFFSET that ($locked$) reference point down by MOD(X, 19), and XLOOKUP the result. 
Knowing the Reward table will be referenced frequently, 'symbol' and 'amount' named ranges were given to the Item and Base Pts columns of the Rewards table.

![](https://github.com/blanchardmike/FMWC/blob/main/Resources/FMWC_Q1_formula.png)
