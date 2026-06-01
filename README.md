# CASA Colonist Rating

Author: Shitian Zhang

This repository is for calculating the performance of CASA players in [Colonist](https://colonist.io/).

See [main.ipynb](main.ipynb) for the code and results.

## Latest Results

Until: 28 May 2026

|ID        |Skill μ|Skill σ|Raw Rating|Attendance Multiplier|Final Rating|
|----------|-------|-------|----------|---------------------|------------|
|Nuzzi1445 |27.156 |2.674  |19.133    |1.0                  |19.133      |
|RobotZhang|25.285 |2.804  |16.872    |0.95                 |16.028      |
|siskiUmax |24.777 |3.03   |15.687    |0.95                 |14.903      |
|Reniti9594|23.776 |2.847  |15.236    |0.95                 |14.474      |
|Linoel4818|25.604 |3.451  |15.25     |0.7                  |10.675      |
|Clay6603  |23.358 |5.728  |6.176     |1.0                  |6.176       |
|Bitbat93  |17.404 |4.198  |4.81      |1.0                  |4.81        |
|Hersch0784|19.677 |4.41   |6.448     |0.7                  |4.513       |


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
