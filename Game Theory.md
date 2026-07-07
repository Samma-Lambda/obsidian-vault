# What is Game Theory
Game theory is the study of strategically interdependent outcomes. This means there is a set of players who's actions effect one another. Its important to note that game does not need to be one where there are $n$ winners and $m$ losers, it can just be a system of players trying to maximize their payout. This allows us to generalize this theory to more complicated scenarios such as businesses and negotiations. We are assuming that the players in our models are perfectly rational 
## Types of Games
### **Strategic/Simultaneous Game:** 
This is where all players make their decision about their strategy once before seeing what other players are doing, without any knowledge of what other players strategies are. Formally its a set of
1. a set of $N$ players 
2. For each player a set of actions available to the player denoted $A_i$ 
3. For each player there is a preference relation for each player denoted $\succ$ on the set $A$ which is the cartesian product of all the $A_i$'s 
Basically we have a set of players which are going to decide their strategy, and each one wants the best outcome according to their ranking, but the outcome depends on other players strategies. 
Often times we can simplify the ranking by using a payoff function $u:A\rightarrow \mathbb{R}$ 
## Types of Strategy
- **Pure Strategy:** This is where you make a single decision
- **Mixed Strategy:** This is where you have a distribution of strategies you are going to use

# Strict Dominance 
![[Pasted image 20260613135915.png|374]]
We are going to use the prisoners dilemma to show an example of strict dominance. We are going to assume that both players are greedy thus their only goal it to maximize their score. If player $2$ keeps quiet then the best move for player $1$ to make would be to confess, if player $2$ confesses then the best move for player $1$ to make would be to confess again.
Thus in every situation player $1$ is better off confessing, because confessing strictly dominates keeping quiet.

A mixed strategy strictly dominates a pure strategy or another mixed strategy if 

# Iterated Elimination of Strictly Dominating Strategies
![[Screenshot 2026-06-13 at 2.07.11 PM.png|377]]
Iterated Elimination of Strictly Dominating Strategies is a form of "preprocessing" before analyzing a game. It looks for strictly dominating situations and then eliminates them reducing our game into a smaller more understandable game. 

For example for the red player going center always does better than going right thus we can eliminate the right column. Then with our simplified game we can do this process again, resulting in the blue player realizing that middle now strictly dominates down. We can do this again and again until we can't anymore. You can repeatedly do this on the example to then find out that the only viable game is middle center. 

This can be further extended into mixed strategies. If you have a mixed strategy that strictly dominates a pure strategy than we can entirely eliminate the strategy. 

# Pure/Mixed Nash Equilibrium
A Nash equilibrium is a set of decisions that players made, in which no player would choose to change their choice. An example would be in this payoff matrix
![[Screenshot 2026-06-13 at 3.44.56 PM.png|438]]
If both players choose to hunt the stag neither of them would choose to change their decision, same with if they both choose to hunt the hare. 
We know a state is a pure state Nash equilibrium if both players are doing the best response to the other players action.  
Looking at mixed strategies, a Mixed Nash Equilibrium is a set of mixed strategies in which any change would result in a lower expected payoff. 
## What is the significance of a Nash Equilibrium
These Nash Equilibriums explain why there are states players stay in, desipite there being better situations 