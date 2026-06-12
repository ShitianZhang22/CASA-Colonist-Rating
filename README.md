# CASA Colonist Rating

Author: Shitian Zhang

This repository is for calculating the performance of CASA players in [Colonist](https://colonist.io/).

See [main.ipynb](main.ipynb) for the code and results.

## Latest Results

Until: 12 June 2026

|ID        |Skill μ|Skill σ|Raw Rating|Attendance Multiplier|Final Rating|
|----------|-------|-------|----------|---------------------|------------|
|Nuzzi1445 |25.54  |2.44   |18.219    |1.0                  |18.219      |
|RobotZhang|26.064 |2.546  |18.425    |0.95                 |17.504      |
|siskiUmax |25.406 |2.709  |17.28     |1.0                  |17.28       |
|Reniti9594|23.72  |2.554  |16.058    |1.0                  |16.058      |
|Linoel4818|24.629 |3.039  |15.513    |0.95                 |14.738      |
|Bitbat93  |20.572 |3.493  |10.094    |1.0                  |10.094      |
|Clay6603  |20.9   |5.025  |5.826     |0.95                 |5.535       |
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
