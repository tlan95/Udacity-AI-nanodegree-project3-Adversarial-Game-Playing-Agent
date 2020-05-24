# Udacity Artificial Intelligence Nanodegree Project3: Adversarial Game Playing Agent
My solution for Udacity AI nanodegree project3-Adversarial Game Playing Agent



# Build an Adversarial Game Playing Agent

![Example game of isolation on a square board](viz.gif)

## Synopsis

In this project, I will experiment with adversarial search techniques by building an agent to play knights Isolation.  Unlike the examples in lecture where the players control tokens that move like chess queens, this version of Isolation gives each agent control over a single token that moves in L-shaped movements--like a knight in chess.

### Isolation

In the game Isolation, two players each control their own single token and alternate taking turns moving the token from one cell to another on a rectangular grid.  Whenever a token occupies a cell, that cell becomes blocked for the remainder of the game.  An open cell available for a token to move into is called a "liberty".  The first player with no remaining liberties for their token loses the game, and their opponent is declared the winner.

In knights Isolation, tokens can move to any open cell that is 2-rows and 1-column or 2-columns and 1-row away from their current position on the board.  On a blank board, this means that tokens have at most eight liberties surrounding their current location.  Token movement is blocked at the edges of the board (the board does not wrap around the edges), however, tokens can "jump" blocked or occupied spaces (just like a knight in chess).

Finally, agents have a fixed time limit (150 milliseconds by default) to search for the best move and respond.  The search will be automatically cut off after the time limit expires, and the active agent will forfeit the game if it has not chosen a move.

**You can find more information (including implementation details) about the in the Isolation library readme [here](/isolation/README.md).**


## Getting Started (Workspaces)

The easiest way to complete the project is to use the Udacity Workspace in your classroom. The environment has already been configured with the required files and libraries to support the project. If you decide to use the Workspace, then you do NOT need to perform any of the setup steps for this project. Skip to the section with instructions for completing the project.


## Getting Started (Local Environment)

If you would prefer to complete the exercise in your own local environment, then follow the steps below:

- Open your terminal and activate the aind conda environment (OS X or Unix/Linux users use the command shown; Windows users only run `activate aind`)
```
$ source activate aind
```

- Download a copy of the project files from GitHub and navigate to the project folder. (Note: if you've previously downloaded the repository for another project then you can skip the clone command. However, you should run `git pull` to receive any project updates since you cloned the repository.)
```
(aind) $ git clone https://github.com/udacity/artificial-intelligence
(aind) $ cd "artificial-intelligence/Projects/3_Game Playing"
```


## Instructions

You must implement an agent in the `CustomPlayer` class defined in the `game_agent.py` file. The interface definition for game agents only requires you to implement the `.get_action()` method, but you can add any other methods to the class that you deem necessary.  You can build a basic agent by combining minimax search with alpha-beta pruning and iterative deepening from lecture.

**NOTE:** Your agent will **not** be evaluated in an environment suitable for running machine learning or deep learning agents (like AlphaGo); visit an office hours sessions **after** completing the project if you would like guidance on incorporating machine learning in your agent.

#### The get_action() Method
This function is called once per turn for each player. The calling function handles the time limit and 
```
def get_action(self, state):
    import random
    self.queue.put(random.choice(state.actions()))
```

- **DO NOT** use multithreading/multiprocessing (the isolation library already uses them, which may cause conflicts)
- **ALL** of the functions you add should be created as methods on the CustomPlayer class. Avoid nested classes & functions, especially for long-running procedures, as these may cause your agent to block the automatic timeout when your turn ends.


## Experiment


### Develop a custom heuristic (must not be one of the heuristics from lectures, and cannot only be a combination of the number of liberties available to each agent)

- Create a performance baseline using `run_search.py` (with the `fair_matches` flag enabled) to evaluate the effectiveness of your agent using the #my_moves - #opponent_moves heuristic from lecture
- Use the same process to evaluate the effectiveness of your agent using your own custom heuristic
    
**Hints:**
- Research other games (chess, go, connect4, etc.) to get ideas for developing good heuristics
- If the results of your tests are very close, try increasing the number of matches (e.g., >100) to increase your confidence in the results
- Experiment with adding more search time--does adding time confer any advantage to your agent over the baseline?
- Augment the code to count the nubmer of nodes your agent searches--is it better to search more or fewer nodes? How does your heuristic compare to the baseline heuristic you chose?


## Report Requirements

Your report must include a table or chart with data from an experiment to evaluate the performance of your agent as described above.  Use the data from your experiment to answer the relevant questions below. 

**Advanced Heuristic**
- What features of the game does your heuristic incorporate, and why do you think those features matter in evaluating states during search?
- Analyze the search depth your agent achieves using your custom heuristic. Does search speed matter more or less than accuracy to the performance of your heuristic?

