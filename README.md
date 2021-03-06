# Omweso Agent

## Synopsis

Omweso is a board game part of a family of other variants in the Mancala family, originating from the people of Uganda. The game is played on a board with 4 rows and 8 columns of pits, where seeds are initially placed and sowed throughout the game. Each player begins with 32 seeds which can be placed in any conformation they deem strategical in their corresponding 2 x 8 grid of pits. Following the preliminary setup with all 32 seeds of each player positioned in the pits of the board, the game begins. The player decides on the move to be played, which consists of picking up all the seeds from one pit containing more than 1 seed on their side of the board, and sowing them in a counter-clockwise manner, until there are no more seeds in that set. At this point, the player's turn could end, relay sowing could follow or a capture could occur. The ultimate goal of the game is to capture the opponent's seeds such that no more moves can be made, meaning that all of the opponent's pits contain 1 seed or less. In order to design a competitive agent, many approaches are explored during this experiment. Greedy algorithms are initially used with the endeavour to snatch possession of the opposing player's seeds. Minimax game algorithm is implemented in order to infer potential moves with the assumption that the opponent plays in an optimal manner. Alpha-Beta Pruning is also employed in order to cut down space and time complexity and increase the depth of the searching algorithm. The Monte Carlo method is considered and its approach discussed. The concepts of randomness and chaos are also included to maximize the winning probability. Results of each implementation are used to assess the efficiency of the AI agent. 

## Code Example

Pseudocode for Minimax algorithm:

```java
Minimax(boardstate, depth, turnPlayer)
    if(depth is 0 || moveList is empty)
        return difference in number of seeds
    if(turnPlayer true)
        get list of legalMoves
        for move M in legalMoves:
            bs = simulate move M
            score = Minimax(bs, depth-1, false)
        return bestMove
    if(turnPlayer false)
        get list of legalMoves
        for move M in legalMoves:
            bs = simulate move M
            score = Minimax(bs, depth-1, true)
        return bestMove
        
```

Pseudocode for Alpha-Beta Pruning Algorithm:

```java
AB(boardstate, depth, a, b, turnPlayer)
    if(depth is 0 || moveList is empty)
        return difference in number of seeds
    if(turnPlayer true)
        get list of legalMoves
        for move M in legalMoves:
            bs = simulate move M
            score = AB(bs, depth-1, a, b, false)
            a = Max(a, score)
            if(b <= a)
                break
        return bestMove
    if(turnPlayer false)
        get list of legalMoves
        for move M in legalMoves:
            bs = simulate move M
            score = AB(bs, depth-1, a, b, true)
            b = Max(b, score)
            if(b <= a)
                break
        return bestMove
        
```

## Motivation

Several approaches have been considered and combined together in the process of creating the AI agent. After each implementation of a new algorithm or concept, tests have been run in order to obtain data for efficiency assessment. Depending on the results, the method tends to change accordingly. Hence, there is a motivation behind every step throughout the conception of the agent. Overall, the approach can be defined as a deep-searching engine which implements touches of randomness.

#### Greedy, Greedier, Greediest
The first attempt of creating an Omweso agent is to implement the logic based on greedy heuristics. Given that the agent plays a particular move, the algorithm returns the best decision according to greedy evaluation functions. The initial motivation behind this choice of method is because of speed and complexity. Supposing that the greedy algorithm does indeed return an optimal solution, it would be much faster and computationally more efficient than other extensive heavy-weight algorithms. 

#### The Deepest Wins
Discussed in the results section, the greedy approach does not seem to be the best, nowhere near perfect. In the case of Omweso, the greedy algorithms fail to find the globally optimal solution, as it only considers the impact of a move one step ahead. To remedy this issue, the concept of searching through the game-tree comes to mind. Minimax is an adequate algorithm to be implemented in 2-player board games, as it tries to maximize and minimize possible moves from the player and the opponent, respectively. To increase the depth and enhance the time and space complexity, Alpha-Beta Pruning algorithm is used. The motivation is that if the agent can search and look at outcomes further ahead than the opponent, there is a lower risk of choosing a move that leads to an eventual loss. 

#### Chaotic Behavior, Unexpected!
Having the impression that many classmates are also designing agents based on Minimax algorithms, the battles could be close and the outcome would mainly be defined by the depth of the search engine and the initial placement of the seeds. What if a touch of randomness is included? The reason behind this approach is based on the effect of suprise, when the opposing player does no expect an non-optimal move to be played. Hence, by including some chaos in the functionality and logic of the player, it might throw the opponents off. Doing so, slightly worse outcomes at early levels are not completely omitted.


