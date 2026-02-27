# CS-370-Current-and-Emerging-Trends

Overview
--------

This project implements a **Deep Q-Learning (DQN)** agent that learns to solve a maze-based Treasure Hunt game using reinforcement learning.

The pirate agent must learn to reach the treasure from any valid starting position — without being explicitly programmed with the solution path.

Instead of hardcoding logic, the agent learns optimal behavior through:

*   Reward feedback
    
*   Experience replay
    
*   Neural network function approximation
    
*   Exploration vs exploitation (epsilon-greedy policy)
    
*   Target network stabilization
    

The full training process and outputs are available in the exported Jupyter Notebook:

Environment Description
-----------------------

*   8×8 maze grid
    
*   1.0 → walkable path
    
*   0.0 → wall
    
*   Bottom-right cell → treasure
    
*   Agent receives:
    
    *   Reward for reaching treasure
        
    *   Penalty for invalid moves
        
    *   Penalty for inefficient movement
        

The agent must learn the best path from _any_ free cell.

Neural Network Architecture

This project uses a Deep Q-Network instead of a traditional Q-table.

Model Structure
model = Sequential()
model.add(Dense(maze.size, input_shape=(maze.size,)))
model.add(PReLU())
model.add(Dense(maze.size))
model.add(PReLU())
model.add(Dense(num_actions))
model.compile(optimizer='adam', loss='mse')

Input: Flattened maze state

Hidden Layers: Dense + PReLU activation

Output: Q-values for 4 possible actions (LEFT, UP, RIGHT, DOWN)

Loss Function: Mean Squared Error

Optimizer: Adam

Architecture
------------

This project uses a **Deep Q-Network (DQN)** instead of traditional Q-table learning.

### Neural Network Structure

* model = Sequential()  
* model.add(Dense(maze.size,input_shape=(maze.size,)))  
* model.add(PReLU())  
* model.add(Dense(maze.size))  
* model.add(PReLU())  
* model.add(Dense(num_actions))   


*   Input: Flattened maze state
    
*   Hidden layers: Dense + PReLU activations
    
*   Output: Q-values for 4 possible actions (LEFT, UP, RIGHT, DOWN)
    
*   Loss: Mean Squared Error
    
*   Optimizer: Adam
    
*   Reinforcement Learning Strategy
    
*   Epsilon-Greedy Exploration
    
*   epsilon = 1.0epsilon\_decay = 0.995epsilon\_min = 0.05
    
*   High exploration early
    
*   Gradual decay toward exploitation
    
*   Minimum epsilon prevents total greediness
    

Reinforcement Learning Strategy
-------------------------------

### Epsilon-Greedy Exploration

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   epsilon = 1.0  epsilon_decay = 0.995  epsilon_min = 0.05   `

*   High exploration early
    
*   Gradual decay toward exploitation
    
*   Minimum epsilon prevents total greediness
    

### Experience Replay

The agent stores episodes as:

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   [state, action, reward, next_state, game_over]   `

Experience replay:

*   Reduces correlation between samples
    
*   Improves learning stability
    
*   Allows batch training
    

Training Loop
-------------

Training includes:

*   Random start positions
    
*   Batch updates via @tf.function optimized training step
    
*   Target network synchronization
    
*   Win rate tracking
    
*   Early stopping when 100% completion achieved
    

Early stopping condition:

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   if win_rate >= 0.999 and completion_check(model, maze):   `

This ensures the agent can solve the maze from all valid starting cells.

Results
-------

During training:

*   Win rate increases steadily
    
*   Loss decreases as Q-values converge
    
*   Agent learns shortest path strategies
    
*   Successfully generalizes across starting positions
    

After convergence:

*   100% win rate
    
*   Completion check passes
    
*   Agent reliably reaches treasure
    

Technologies Used
-----------------

*   Python
    
*   TensorFlow
    
*   Keras
    
*   NumPy
    
*   Matplotlib
    
*   Custom Environment (TreasureMaze)
    

Possible Improvements
---------------------

Future enhancements could include:

*   Double DQN
    
*   Prioritized Experience Replay
    
*   Dueling Networks
    
*   Reward shaping experiments
    
*   Larger maze generalization
    
*   Visualization of Q-value heatmaps
    
*   Training curve plotting
