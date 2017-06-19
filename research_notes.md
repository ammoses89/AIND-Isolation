### Notes

All games of _perfect_ information have a optimal value function $v^*(s)$ 

- determines outcome of game from board position, or state $s$ 
- can be solved by recursively computing the optimal value function in a search tree of $ {b^d} $ possible sequences, where $b$ is the game's breadth (legal moves per position) and $d$ is the game's depth (game length)
  - chess ($$b \approx 35, d \approx 80 $$) and go ($$ b \approx 250, d \approx 150 $$)
  - exchaustive search is infeasible for chess  and go
  - But search space can be reduced by two general principles
    1. Reduce search depth by position evaluation: replace the substree below state $s$ with an approximate value function $$ v(s) \approx v^*(s) $$ (this has lead to breakthrough performance in chess, checkers, and othello. but not Go because of the game's complexity)
    2. Reduce search breadth by sampling possible moves from a state $s$ and averaging over positions to build a position evaluation (this has led to breakthrough performance  in backgammon and Scrabble)



Monte Carlo Tree Search (MCTS) uses *rollouts* to estimate the value of each state in a search tree.

  **Goal** 

Build a state of the art AI solution to solve and win Go games. 

- Not yet has there been an effective way to evaluate the best position and find the best move for a game as complex as Go. 
- Monte Carlo Tree Search is used by the state of art Go programs due to it's ability to provide a value function without branching (by similating a game until completion then backproprogating the result to update the tree)

   **Techniques** 

Use neural networks to calulcate the board positions and select the best move.

- Use of Supervised Learning to provide a probability distribution
  - 13 layer "policy" network (policy is the action/move to choose for state/position)
  - trained from 30 million positions from KGS Go dataset
  - Stochastic Gradient Ascent (SGA) to maximize move chosen from position (expected outcome)
  - accuracy of 57%
- Reinforcement learning of simulated games between the current policy network (trained SL network) and previous iterations of the policy network (earlier epochs/iterations of the SL network during training)
  - weights are initilized to the SL network's resulting weights
  - plays against random iterations of SL network, which would have different weights at different points of training.
  - each game is rewarded a $+1$ for winning and a $-1$ for losing
  - these rewards are used to update the weights at each time step $t$ , or each game
  - evaluated by choosing a move from a probability distribution of possible moves
    - won 80% of the time against the SL network
    - won 85% against the Pachi program
- Reinforcement learning of the policy network playing itself to determine the best move (value network)
  -  outputs a single prediction instead of probablity distribution
    - - trained with SGD and MSE using regression and state-outcome pairs as input data
      - generated positions from the RLp network playing itself
    - Combination of the policy network (SL->RLp) and the value network (RLv) in an MTCS algorithm that selects moves by a lookahead search
      - Each traversal is a simulation (game played to completion)
      - used to build value function



**Evaluation**

- Evaluated against state of the art Go programs: Crazy Stone, Zen, Pachi, and Fuego. All based on MTCS algorithms. (Won 494/495 games )
- Evaluated against Fan Hui (Won 5/5 games)


- Distributed Version performed better than single-machine version by winning 100% against the other Go programs.

