# Student Data

**Name**: Diogo Cosin Ayres de Oliveira

**Course**: Data Engineering Masters

# SIR Model with Default Values

First of all, let's see the SIR model time reponse with the following default parameters:

| Parameter | Value  |
| --------- | -----: |
| c         |    1.0 |
| a         |  0.025 |
| $\rho$    |   0.03 |
| d         |   0.1  |
| $\sigma$  |   0.3  |
| $\theta$  |   0.15 |
| $\delta$  |   0.25 |

Plotting the first 60 days of the SRI model time response, we get the following graph.

<img src="images/default_values.png" width="450">

The graph show that after approximately 20 days, almost all 100 individuals will be dead. This may be explained by the fact that the death rate of healthy individuals `d` is 0.1 per day, that is, 10% of all healthy individuals will die. At the beggining, this is equivalent to 8 individuals.

# SIR Model with all Parameters equal Zero

This extreme scenario would be a permanent state, that is, no changes on individuals dying, getting infected or recovered and immigrating since all parameters are set to zero. To check, let's see the time response plot.

<img src="images/zeros_values.png" width="450">

As expected, all individuals levels remain the same as the initial conditions.

# Checking the `c` Parameter Influence

By default the `c` is set to 1, meaning that every susceptible will necessarily be in contact with an infected individual. Let's change this parameter to 0.5.

<img src="images/c0.5.png" width="450">

Now the populations takes slightly longer to decrease, but it is still almost completely eliminated as it happens using `c = ` 1.0 and the default parameters.

Finally let's check the extreme case where no susceptible individual will be in contact with infected individuals, in other words, `c = ` 0.

<img src="images/c0.png" width="450">

In this case, as susceptible people are not getting infected, they will die according to the `d` parameters and not to $\delta$ parameters. This means that, at the default parameters configuration, they will die at the slower rate 0.1 and not 0.25.

# Checking the `a` Parameter Influence

Let's check how the probability of transmission of the disease upon contact, `a`, affects the SIR model time reponse. For this, let's set the extreme value 1 to it, meaning that every individual who contacted to an infected individual will certainly get infected as well. The other parameters are set to the default values.

<img src="images/a1.png" width="450">

As expected, right at the first day, all susceptible individuals get infected, elevating the infected population to more than 80 individuals. After that, with 25% of the infected population dying each day, it takes less than 25 days to almost completely eliminate the whole population.

# Checking the $\rho$ Parameter Influence

Let's check what it the model's behaviour when all infected individuals get recovered, that is, $\rho$=1. Intuitively, the number of recovered individuals should increase, but they will still die according to `d` parameter.

<img src="images/p1.png" width="450">

Indeed, there are more recovered individuals, but still the population is almost completely eliminated after 60 days.

Now let's check what happens when the individual cannot be recovered, $\rho$=1.

<img src="images/p0.png" width="450">

In this scenario, there are no recovered individuals besides the five intials ones. Also, the population is eliminated faster within 20 days.

# Checking the Influence of the `d` Parameter

Let's imagine that humanity has evolved to a level where only 0.1% of healthy people die. That way we would obtain the following time response in the SIR model.

<img src="images/d0_001.png" width="450">

That's an interisting result. After around 30 days, when there is no longer infected individuals as they all died, the population begins to grow again. This may explained by the fact that there a new people coming according to the $\theta$ parameter and fewer people diying, as `d` was set to a low value.

# Checking the Influence of the $\sigma$ Parameter

Let's consider that we are modelling a disease which it is not possible to get infected twice, that is, let's set $\sigma$ parameter to 0 and see the time response.

<img src="images/sigma0.png" width="450">

Now that recovered individual can't be infected again, their population increases and dies according to the `d` parameter.

# Checking the Influence of the $\theta$ Parameter

In mass immigration cases, $\theta$ would assume higher values. For instance, let's visualize the model behaviour when $\theta$ is set to 10.

<img src="images/theta10.png" width="450">

In that case, it is possible to notice that immigrants are feeding the disease to a point that the number of individuals stabilize after 20 days with the majority infected. In other words, the individuals are dying, but, as there is always new individuals coming in, the populations is not eliminated.

# Checking the Influence of the $\delta$ Parameter

Now let's play with an unrealistic situation: infected individuals acquire superpowers and, because of that, they do not die. In the SIR model, this means setting $\delta$ to 0. The following time response is obtained in thus case.

<img src="images/delta0.png" width="450">

Infected individuals do not die, but they are still recovered according to the $\rho$ parameter, consequently, after recovered, they die accordind to the `c` parameter.

Let's not allow individuals to be recovered setting $\rho$ to 0 in order to check whether the previous conclusion is valid. In this configuration, we obtain the following time response.

<img src="images/delta0rho0.png" width="450">

Accordingly to what was previously discussed, now that there is no recover chance to infected individuals and they don't die, the infected population grows to infinite due to the immigated new susceptible individuals while the healthy population is completely eliminated in less than 10 days.
