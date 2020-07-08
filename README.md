# Deep Reinforcement Learning Nanodegree Project 2: Continuous Control


## Introduction

<img src="https://user-images.githubusercontent.com/10624937/43851024-320ba930-9aff-11e8-8493-ee547c6af349.gif" alt="Trained Agent" title="Trained Agent" style="max-width:100%;">

The files in this repository implement a DDPQ agent acting in the <a href="https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#reacher">Reacher</a> environment, where an agent controls a double-jointed arm with the goal of pointing toward a moving target.

This implementation works with two versions of this environment:

 - **Single agent:** train the agent to achieve an average score of +30 over 100 consecutive episodes.
 - **Distributed (20 identical) agents:** each agent operates in its own copy of the environment and the group is collectively trained until achieving an average score of +30 (over 100 consecutive episodes, and over all agents).

The environment is set up as follows:

 - **Reward:** +0.1 is earned for each step during which the agent's hand is in the goal location.
 - **Obserfaction space:** consists of 33 variables corresponding to position, rotation, velocity, and angular velocities of the arm. Each action is a vector with four numbers, corresponding to torque applicable to two joints. Every entry in the action vector should be a number between -1 and 1.

The contents in the Continuous_Control.ipynb file solve the second version of this environment.

## Getting Started
1. Clone this repository.

2. Download the environment from one of the links below. You need only select the environment that matches your operating system:

 - **Version 1:** Single Agent

    - **Linux:** <a href="https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Linux.zip">click here</a>
    - **Mac OSX:** <a href="https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher.app.zip">click here</a>
    - **Windows (32-bit):** <a href="https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Windows_x86.zip">click here</a>
    - **Windows (64-bit):** <a href="https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Windows_x86_64.zip">click here</a>

- **Version 2:** Distributed Agents (20)

    - **Linux:** <a href="https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Linux.zip">click here</a>
    - **Mac OSX:** <a href="https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher.app.zip">click here</a>
    - **Windows (32-bit):** <a href="https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86.zip">click here</a>
    - **Windows (64-bit):** <a href="https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86_64.zip">click here</a>

 - **AWS:** If you'd like to train the agent on AWS (and have not enabled a virtual screen), use <a href="https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Linux_NoVis.zip">this link</a> (version 1) or <a href="https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Linux_NoVis.zip">this link</a> (version 2) to obtain the "headless" version of the environment. You will not be able to watch the agent without enabling a virtual screen, but you will be able to train the agent. (To watch the agent, you should follow the instructions to enable a virtual screen, and then download the environment for the Linux operating system above.)

3. Place the downloaded file(s) in the folder you cloned this repo to and unzip (or decompress) the file.

4. Create a Python environment for this project, *e.g.*, using conda or venv.

5. Activate that environment and install dependencies: <code>pip install -r requirements.txt</code>

## Instructions
1. Open the <code>Continuous_Control.ipynb</code> notebook and adjust the path to your desired environment file based on its name and where you placed it.

2. You are ready to start interacting with the environment.
 - Use the cells in sections 1, 2 and 3 to initialize and explore the environment
 - Run the cells in section 4 to train the agent. Feel free to change the hyperparameters in <code>ddpg_agent.py</code> to see if you can improve training.
 - Run the cells in section 5 to test the agent.
