# dicegame
Choice of Algorithm:  
I attempted to follow the methods and functions given in Analysis Mode from the notebook.  
This method looks at all possible outcomes given a state i.e. a dice roll of 2, 3, 4.  
  
Given this, we can find all possible outcomes, for every given state and action, using the method get_next_states(action, dice_state). From this we can extract the probability of each state occurring and the reward value.  
  
This method is applied in analysis_mode, where a dictionary of actions has been instantiated, with the intention of attributing a reward for each action, given a state.
To achieve this, we iterate through each action (again using the helper methods from dice_game) and for those actions get the reward value - probability * (reward + gamma), gamma being the discount rate. If the game is over (terminal state - no further actions allowed) we can set this reward value to the action in the dictionary, if the game is not over we use the Bellman Equation to get the sum of rewards. The dictionary is updated with the result of that action.  
  
Value iteration is created by using the pseudocode provided to find the deterministic policy. We initialise a dictionary instead of an array to use states as keys then the optimal policy as its value. We start a loop and set delta as 0, iterate through each state and create a rewards list for each state, then choose the max reward value. Delta is set with either delta or the absolute difference between the max value and previous max value for that state. This is repeated until the values have converged and delta becomes smaller than theta - a chosen small positive number. This is our optimal policy which we can use to achieve the max reward when given a state, as applied in play.  
  
  
The discount rate (gamma) was initially set to 0.9, telling the agent that re-rolling is less desirable due to the penalty, however this led to lower overall rewards. Set at 1 gave the best results, telling the agent to stick at the best possible score.  
