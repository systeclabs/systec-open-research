
## Glossary

### agent
entity that perceives its enviroment and acts upon that environement

### state
a configuration of the agent and its enviroment. e.g.

![[Screen Shot 2023-05-19 at 18.12.03.png]]
### initial state
initial state where the agent stars
* What actinos do we apply to get to the goal
	* by taking actions

### actions
choices that can be made in a state (function)
ACTIONS(s) returns the set of actions that can be executed in state s

![[Screen Shot 2023-05-19 at 18.13.38.png]]

### transition model
description of what state resutls from perfmorin any applciaton action a any 
state
RESULTS(s,a) returns the state resutling from pefrofmain action a in state s

![[Screen Shot 2023-05-19 at 18.15.37.png]]

* statu two dimineswaln array
* actino enums for multiple possiblies

![[Screen Shot 2023-05-19 at 18.16.50.png]]

### state space
thje set of all satte reachable from the initia state by any sequest of actions![[Screen Shot 2023-05-19 at 18.17.26.png]]

can be represetned as a graph
each node represnt a state of a problem
branch can take action to take us from an state to another

### goal test
way to determine wheter a given state is a goal state
* can be 1 initial posiiton and 1 end goal
* can be multiple goals

### path cost
numerical cost assocaited with a given path
* we dont want to take longer paths from intial state to goal state

![[Screen Shot 2023-05-19 at 18.20.35.png]]

## Search Problems

* intial state
* actions
* transition model
* goal state
* paht cost function

### optimal solution
a soluiton that has the lowest path cost among all solutions

### node 
a data struct that keeps track of 
- a state
- a parent (node that generated this node)
- an action (action applied to parent to get node)
- a path cost (from initial state to node)

from a given state we havemultiple options that we can take and we are going to explore those options

consider all avaiable options in a data structure called frontier

frontier
all things we could explore next


## Approach

* Starts with a frontiner that contain intial state
* Repeat:
	* If frontier is empty, then no solution
	* remvoe a node from frontienr
	* if node contains goal state, return the solution
	* expand node, add resulting nodes to the frontier


