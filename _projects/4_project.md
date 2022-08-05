---
layout: page
title: RL based Maze Traverser Agent  
description: An Proximal Policy Optmization based RL agent is trained to navigate a maze bulti using Unity 3D.
img: assets/img/1.jpg
importance: 4
---
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/RL_maze.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
     System responses to gestures
</div>

Unity 3D - a game development platform is used for creating a maze-like environment. ML-agents toolkit, an open-source Unity project is used, which enables the training of the intelligent agents using reinforcement learning or any machine learning methods through a simple-to-use Python API. Every project has a beautiful feature showcase page. Different features of the Unity were utilized to analyze and monitor the performance of the policy optimization e.g. multiple environment spaces were built, creating replicas of the same environment to monitor the speed of convergence while parallel training, played with the Curriculum learning, shaping the rewards i.e. finding the right amount of reward that needs to be assigned for each state-action pair, tweaking the parameters for Ray-perception 3D sensor for the agent and nally gathering the results and analyze the training statistics with the plots.

An algorithm such as PPO is used and the policy with the maximum expected return. There are two types of Stochastic policies that can be used Categorical and Gaussian. In our problem, we use Categorical policies because it supports discrete action space. The goal of RL is to select a policy which maximises the expected return. In order to maximise the policy returns, we need an optimization algorithm like policy gradient.

The motivation behind the invention of PPO relies on the same point as TRPO's, which is how can we take the largest possible step to optimize the policy using the current data without causing any damage to the current policy's performance. In case of TRPO the developers solved this issue by using KL divergence term. However, PPO is a family of first order methods and uses a clipped surrogate objective function to keep new policies closer to the old policy. PPO is an on-policy algorithm which is derived from the TRPO and can be used with the environments having both discrete and continuous action spaces. PPO being an on-policy type, doesn't store any past experiences but instead learns directly by interacting with the environment.

A simple maze environment was built along with the agent and the target. ML-agents toolkit which is an API is used to train the agent using the preimplemented PPO algorithm. Unity provides various features like ray-perception sensor, box colliders. In this maze game, box colliders play an important role in providing obstruction behaviors for the objects. The ray perception sensor is used to project n numbers of rays at specified angles and length, this allows us to detect the objects colliding within the proximity of the rays. Once the environment is built and the above-mentioned features are setup, next step is to collect the observations of the agent from the environment which are inputs to the algorithm. This can be done using the C# script wherein we use the built-in functions. The observations for the agent will be agent's position, target's position, agent's velocity, distance between agent and target and finally the vector consisting the objects detected by the ray perception sensor. We also set the rewards for the possible state-action pair in the script. The hyper-parameters for training the PPO algorithm can be altered if needed using the default yaml config file provided with the ML-agents toolkit. Once all the above steps are completed, we can commence with the training phase. During this training phase, the agent starts exploring the environment space. The policy gets updated only after T(max steps) number of time steps. The episode can end based on two conditions, when the agent reaches the target or when the maximum T steps are encountered. This T max steps should not be confused with the max steps specified in the config file as the later specifies the maximum steps allowed for the entire training process. Once the network is trained, we can use the trained modeles to infer the results. Also, the training statistics can be visualized using the Tensor-board framework.


We were successfully able to implement PPO algorithm in Unity using ML-agents toolkit. Training the agent using curriculum learning is a better way as it allows the network to converge faster. In our case it was almost two times faster which can be seen in the plots below.

During the initial episodes of training, the agent starts exploring the environment and learns to avoid hitting the walls since it gains a negative reward for each collision with the wall (from 0 to 10000 episodes). After 50,000 episodes the agent starts finding the target and then converges to an optimal solution after 180,000 episodes.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/RL_with_cumulative.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
     System responses to gestures
</div>

In our maze game to increase the difficulty level was to move the target further away from the agent. As the target is close to the agent it converges faster around 25,000th episode. After which the diculty level is increased i.e. the target is moved more further away and thus there is a drop in the reward value around 30,000th episode. The same trend continues until around 90,000 episodes. After which it converges to the optimal solution.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/RL_without_cumulative.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
     System responses to gestures
</div>

We successfully solved the maze problem using PPO along with curriculum learning. Curriculum learning along with Rewarding shaping allows the algorithm to converge faster to an optimal policy. Curriculum learning is also found to be viable in case of a dynamic environment for faster convergence. The input features for the neural network are the most important deciding factor that determines the performance of the model, for example in our case the ray perception sensor gathers the right observations(neural network input features) to attain the optimal policy. In this way experimenting with different input features for the neural network and Unity features helped in optimizing the result.
