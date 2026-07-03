# CASA Colonist Rating

Author: Shitian Zhang

This repository is for calculating the performance of CASA players in [Colonist](https://colonist.io/).

See [main.ipynb](main.ipynb) for the code and results.

## Latest Results

Until: 03 July 2026

|ID        |Skill μ|Skill σ|Raw Rating|Attendance Booster|Final Rating|
|----------|-------|-------|----------|------------------|------------|
|Nuzzi1445 |26.1   |2.309  |19.172    |🐑🐑              |21.089      |
|RobotZhang|25.442 |2.389  |18.274    |🐑🐑              |20.102      |
|siskiUmax |25.144 |2.53   |17.554    |🐑🐑              |19.309      |
|Linoel4818|25.225 |2.944  |16.393    |🐑🐑              |18.032      |
|Reniti9594|23.72  |2.554  |16.058    |🐑                |16.861      |
|Bitbat93  |20.283 |3.129  |10.895    |🐑🐑              |11.985      |
|Hersch0784|19.499 |4.16   |7.018     |🐑                |7.369       |
|Clay6603  |20.9   |5.025  |5.826     |🐑                |6.118       |

# History

![Player Ranking History](data/ranking_history.png)
![Final Rating History](data/rating_history.png)
![Raw Rating History](data/raw_history.png)

# Calculation Method

The rating is calculated using the [TrueSkill](https://trueskill.org/) algorithm, which is a Bayesian ranking system that takes into account both the skill level and the uncertainty of each player. The raw rating is calculated as `Skill_μ - 3 * Skill_σ`, which gives a conservative estimate of the player's skill. As a player play more games, their uncertainty (σ) will decrease, and their raw rating will slightly improve in the long run.

The attendance booster applied to the raw rating to get the final rating. It is calculated as follows. You get 🐑 if you attend at least one game in the recent 4 games, or 🐑🐑 if you attend more than two games. Each 🐑 gives you +5%! 

|Attendance in the recent 4 games|Attendance Booster|
|-------------------------------|----------|
|4                              |🐑🐑(+10%)       |
|3                              |🐑🐑(+10%)       |
|2                              |🐑(+5%)       |
|1                              |🐑(+5%)       |
|0                              |0       |

## Setup

Use the following commands to set up the environment:

```
git clone https://github.com/ShitianZhang22/CASA-Colonist-Rating.git
pip install -r requirements.txt
```
