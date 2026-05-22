# CASA Colonist Rating

Author: Shitian Zhang

This repository is for calculating the performance of CASA players in [Colonist](https://colonist.io/).

See [main.ipynb](main.ipynb) for the code and results.

## Latest Results

Until: 22 May 2026

|ID     |Skill μ   |Skill σ           |Raw Rating        |Attendance Multiplier|Final Rating|
|-------|----------|------------------|------------------|---------------------|------------|
|Nuzzi1445|26.601    |2.765             |18.307            |1.0                  |18.307      |
|RobotZhang|25.285    |2.804             |16.872            |1.0                  |16.872      |
|siskiUmax|24.751    |3.209             |15.123            |0.95                 |14.367      |
|Reniti9594|23.585    |2.994             |14.602            |0.95                 |13.872      |
|Linoel4818|25.604    |3.451             |15.25             |0.7                  |10.675      |
|Hersch0784|19.677    |4.41              |6.448             |0.85                 |5.481       |
|Bitbat93|18.347    |4.486             |4.89              |0.95                 |4.645       |
|Clay6603|25.693    |6.725             |5.519             |0.7                  |3.863       |

# History

![Player Ranking History](data/ranking_history.png)
![Player Rating History](data/rating_history.png)

# Calculation Method

The rating is calculated using the [TrueSkill](https://trueskill.org/) algorithm, which is a Bayesian ranking system that takes into account both the skill level and the uncertainty of each player. The raw rating is calculated as `Skill_μ - 3 * Skill_σ`, which gives a conservative estimate of the player's skill. As a player play more games, their uncertainty (σ) will decrease, and their raw rating will slightly improve in the long run.

The attendance multiplier applied to the raw rating to get the final rating. It is calculated as follows. You will not be heavily penalized for missing a game, but if you miss more than 2 games in the recent 4 games, your rating will be significantly reduced.

|Attendance in the recent 4 games|Multiplier|
|-------------------------------|----------|
|4                              |1.0       |
|3                              |0.95       |
|2                              |0.85       |
|1                              |0.7       |
|0                              |0.5       |

## Setup

Use the following commands to set up the environment:

```
git clone https://github.com/ShitianZhang22/CASA-Colonist-Rating.git
pip install -r requirements.txt
```
