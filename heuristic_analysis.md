# Heuristic Analysis



```

                        *************************
                             Playing Matches
                        *************************

 Match #   Opponent    AB_Improved   AB_Custom   AB_Custom_2  AB_Custom_3
                        Won | Lost   Won | Lost   Won | Lost   Won | Lost
    1       Random      40  |   0    37  |   3    40  |   0    37  |   3
    2       MM_Open     33  |   7    30  |  10    27  |  13    34  |   6
    3      MM_Center    38  |   2    38  |   2    39  |   1    40  |   0
    4     MM_Improved   34  |   6    34  |   6    29  |  11    31  |   9
    5       AB_Open     22  |  18    16  |  24    17  |  23    21  |  19
    6      AB_Center    21  |  19    19  |  21    19  |  21    18  |  22
    7     AB_Improved   25  |  15    15  |  25    13  |  27    17  |  23
--------------------------------------------------------------------------
           Win Rate:      76.1%        67.5%        65.7%        70.7%
```



### custom_score (AB_Custom) 

This is heuristic gave a score based on the difference between the opponent moves from the my moves. If the opponent had more remaining moves, the score was negative and if I had more moves remaining, the score was positive. The total win rate was **67.5%** . It performed worse when the opponent used Alphabeta pruning as a move strategy with a win rate of **45.45%**. It performed well when the opponent used minimax algorithm with a a win rate of **85%**. 



*red - games one by me*

*blue - games one by opponent*

![custom_score_1](/Users/adrian/Downloads/custom_score_1.png)



### custom_score_2 (AB_Custom_2)

This is heuristic gave a score based on the squared distance of my position from the center of the board. The total win rate was **65.7%** . It performed worse when the opponent used Alphabeta pruning as a move strategy with a win rate of **40.8%**. It performed _better_ when the opponent used minimax algorithm with a a win rate of **79%**. 

*red - games one by me*

*blue - games one by opponent*



![custom_score_2](/Users/adrian/Downloads/custom_score_2.png)

### custom_score3 (AB_Custom3)

This is heuristic gave a score based on the number of my moves left.  It surprisingly scored the best with a total win rate was **70.7%** . It performed worse when the opponent used Alphabeta pruning as a move strategy with a win rate of **46.6%**. It performed really well when the opponent used minimax algorithm with a a win rate of **87.5%**. 

*red - games one by me*

*blue - games one by opponent*

![custom_score_3](/Users/adrian/Downloads/custom_score_3.png)



### Conclusion

The best performing heuristic was `custom_score 3` and was a very simple score of available moves left. This could mean that either there needs to be more testing of performance or the the other two evalution heuristics could use some improvement.