# Agent-Based-Model-ABM-in-R
Agent-based models are computer simulations used to study the interactions between people, things, places, and time.
This ABM simulates the movement of 1000 agents in a 100x100 grid environment. At each time step, each agent moves one unit in a randomly chosen direction (up, down, left, right, or stay in place). If an agent moves outside the bounds of the environment, it is placed back at the boundary. After 100 time steps, the final positions of the agents are plotted.

# Set up the environment
width <- 100
height <- 100


We are creating a virtual space for our agents to move around in. It is a grid that is 100 units wide and 100 units tall.

# Set up the agents
num_agents <- 1000
We are creating 1000 little virtual creatures that we will call "agents."


# Initialize the positions of the agents randomly
positions <- matrix(runif(num_agents * 2, 0, max(width, height)), ncol = 2)
We are giving each agent a starting position in the virtual space. These positions are chosen randomly, so each agent could start anywhere within the virtual space.

# Set up the movement function
move_agent <- function(x) {
  # Generate random movement
  dx <- sample(-1:1, 1)
  dy <- sample(-1:1, 1)
  
  # Update position, making sure to stay within the bounds of the environment
  x[1] <- max(0, min(width, x[1] + dx))
  x[2] <- max(0, min(height, x[2] + dy))
  
  return(x)
}
This is a special set of instructions that tells each agent how to move. It says that the agent should choose a random number between -1 and 1, and then use that number to move left, right, up, down, or stay in place. It also makes sure that the agent doesn't go outside the boundaries of the virtual space.



# Set up the simulation
num_steps <- 100

We are going to run the simulation for 100 steps, which means each agent will get to move 100 times.

# Run the simulation
for (t in 1:num_steps) {
  for (i in 1:num_agents) {
    positions[i, ] <- move_agent(positions[i, ])
  }
}


This is the main loop of the simulation. For each time step, it tells each agent to move according to the instructions we gave it in the "move_agent" function.

# Visualize the final positions of the agents
plot(positions[, 1], positions[, 2], xlim = c(0, width), ylim = c(0, height))


Finally, we can see where all the agents ended up after 100 time steps. The plot shows the position of each agent on the virtual space.

