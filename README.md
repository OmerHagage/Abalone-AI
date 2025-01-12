# **ABALONE GAME - AI**

<p align="center">
    <img src="docs/project-picture.png" width="100%" />
</p>

This project focuses on implementing various intelligent agents to play the strategic board game **Abalone**. The game’s complexity is tackled using algorithms like Alpha-Beta Pruning, Minimax, and Q-Learning, alongside heuristic evaluations. Statistical analysis is provided to evaluate agent performance and strategies.

---

## **Key Components**

### **Agents**
- [`AbstractAgent.py`](project/agents/AbstractAgent.py): Base class for all agents, defining the interface and common methods.
- [`AlphaBetaAgent.py`](project/agents/AlphaBetaAgent.py): Implements Alpha-Beta pruning with depth-based heuristics.
- [`MinimaxAgent.py`](project/agents/MinimaxAgent.py): Implements the Minimax algorithm for move evaluation.
- [`QlearningAgent.py`](project/agents/QlearningAgent.py): A reinforcement learning agent using Q-Learning.
- [`RandomPlayers.py`](project/agents/RandomPlayers.py): Random agents for baseline comparisons.

### **Heuristics**
- [`Heuristics.py`](project/agents/Heuristics.py): Contains evaluation functions for gameplay strategies (e.g., attack, defense, balance).

### **Training**
- [`QLearningTraining.py`](project/statistics/QLearningTraining.py): Trains the Q-Learning agent and saves the learned Q-values in [`q_learning_data.pkl`](project/statistics/q_learning_data.py).

### **Statistical Analysis**
- [`GameStatistics.py`](project/statistics/GameStatistics.py): Script to compare agents through a series of matches and analyze performance.

### **Game Logic**
Core game engine to simulate matches between agents or between an agent and a user.

---

## Running Guidelines 
1. [Initialization](#Initialization)
2. [Play against our Agent](#Play against our Agent)
3. [Agent vs Agent](#Agent vs Agent)
   1. [Command Format](#Command Format)
   2. [Agents list](#Agents list)
   3. [Heuristics](#Heuristics)
   4. [Common Commands Examples](#Common Commands Examples)
4. [Statistics](#Statistics)
   1. [Command Format](#Command Format)
   2. [Common Commands Examples](#Common Commands Examples)

   
# Initialization
First, run those commands:
    
    cd <path_to_main_dir>
    virtualenv newEnv --python python3
    source newEnv/bin/activate.csh
    pip install -r requirements.txt

Make sure that all packages are installed successfully.

# Play against our Agent (Please try it!)
For playing against our awesome Agent (AlphaBeta Agent with depth 2) run-

     python3 -m project.game.UserVsAlphaBeta

If you by mistake won our agent please let us know, this agent is top notch.
# Agent vs Agent

## Command Format 

The command format is - 
`python3 -m project.game.AgentVsAgent FirstAgent [Heuristic Depth] SecondAgent [Heuristic Depth]`

While Heuristic and Depth are mandatory parameters for the MiniMax/AlphaBeta Agents and redundant for the others.

The first agent is the white player, the second is the black player.

Legal Examples - 

            Minimax defense 2         
            RandomPrioritize         
            
Illegal Examples-

            AlphaBeta                 
            RandomPrioritize attack 1 

## Agents list
Agents List -

    Random
    RandomPrioritize
    AlphaBeta
    Minimax
    QLearningAgent

## Heuristics
Heuristics Lists-

    defense
    attack
    balance

## Common Commands Examples

Commands:

    python3 -m project.game.AgentVsAgent AlphaBeta attack 2 RandomPrioritize
    
    python3 -m project.game.AgentVsAgent AlphaBeta attack 2 Minimax defense 2
    
    python3 -m project.game.AgentVsAgent RandomPrioritize AlphaBeta balance 1
    
    python3 -m project.game.AgentVsAgent AlphaBeta attack 1 Random
    
    python3 -m project.game.AgentVsAgent QLearning Random
    
#Statistics

## Command Format 

The command format is - 

`python3 -m project.statistics.GameStatistics FirstAgent [Heuristic Depth] SecondAgent [Heuristic Depth]  NumberOfGames`

While Heuristic and Depth are mandatory parameters for the MiniMax/AlphaBeta Agents and redundant for the others.

The first agent is the white player, the second is the black player.

## Common Commands Examples

Commands:

    python3 -m project.statistics.GameStatistics AlphaBeta attack 2 RandomPrioritize 5
    
    python3 -m project.statistics.GameStatistics AlphaBeta attack 2 Minimax defense 2 10
    
    python3 -m project.statistics.GameStatistics RandomPrioritize AlphaBeta balance 1 10
    
    python3 -m project.statistics.GameStatistics AlphaBeta attack 1 Random 1