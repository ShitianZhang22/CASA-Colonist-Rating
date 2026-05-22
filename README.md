# CASA Colonist Rating

Author: Shitian Zhang

This repository is for calculating the performance of CASA players in [Colonist](https://colonist.io/).

See [main.ipynb](main.ipynb) for the code and results.

## Latest Results

Until: 15 May 2026

|ID     |Skill_μ   |Skill_σ           |Raw_Rating        |Attendance_Multiplier|Final_Rating|
|-------|----------|------------------|------------------|---------------------|------------|
|Nuzzi1445|27.94374377278253|2.914769637630226 |19.199434859891852|1.0                  |19.199434859891852|
|RobotZhang|26.011465550644928|2.9652996663397944|17.115566551625545|1.0                  |17.115566551625545|
|siskiUmax|24.011737540790087|3.398805040379249 |13.81532241965234 |0.95                 |13.124556298669722|
|Reniti9594|22.43442012690248|3.155657240376442 |12.967448405773155|0.85                 |11.02233114490718|
|Linoel4818|25.51792694421736|3.6946061584549055|14.434108468852646|0.5                  |7.217054234426323|
|Hersch0784|19.677529328582256|4.957493225186356 |4.805049653023188 |0.85                 |4.084292205069709|
|Bitbat93|17.933512582145365|5.0372690628450085|2.8217053936103405|0.85                 |2.398449584568789|

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
