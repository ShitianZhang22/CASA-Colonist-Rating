# CASA Colonist Rating

Author: Shitian Zhang

This repository is for calculating the performance of CASA players in [Colonist](https://colonist.io/).

See [main.ipynb](main.ipynb) for the code and results.

## Latest Results

Until: 15 May 2026

|ID     |Skill μ   |Skill σ           |Raw Rating        |Attendance Multiplier|Final Rating|
|-------|----------|------------------|------------------|---------------------|------------|
|Nuzzi1445|27.944    |2.915             |19.199            |1.0                  |19.199      |
|RobotZhang|26.011    |2.965             |17.116            |1.0                  |17.116      |
|siskiUmax|24.012    |3.399             |13.815            |0.95                 |13.125      |
|Reniti9594|22.434    |3.156             |12.967            |0.85                 |11.022      |
|Linoel4818|25.518    |3.695             |14.434            |0.5                  |7.217       |
|Hersch0784|19.678    |4.957             |4.805             |0.85                 |4.084       |
|Bitbat93|17.934    |5.037             |2.822             |0.85                 |2.398       |

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
