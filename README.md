# CASA Colonist Rating

Author: Shitian Zhang

This repository is for calculating the performance of CASA players in [Colonist](https://colonist.io/).

See [main.ipynb](main.ipynb) for the code and results.

## Latest Results

Until: 19 June 2026

|ID        |Skill μ|Skill σ|Raw Rating|Attendance Multiplier|Final Rating|
|----------|-------|-------|----------|---------------------|------------|
|Nuzzi1445 |25.519 |2.391  |18.346    |1.0                  |18.346      |
|RobotZhang|26.242 |2.513  |18.702    |0.95                 |17.767      |
|siskiUmax |24.952 |2.642  |17.025    |1.0                  |17.025      |
|Linoel4818|25.225 |2.944  |16.393    |0.95                 |15.573      |
|Reniti9594|23.72  |2.554  |16.058    |0.95                 |15.255      |
|Bitbat93  |20.347 |3.363  |10.259    |1.0                  |10.259      |
|Clay6603  |20.9   |5.025  |5.826     |0.85                 |4.952       |
|Hersch0784|19.499 |4.16   |7.018     |0.7                  |4.913       |

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
