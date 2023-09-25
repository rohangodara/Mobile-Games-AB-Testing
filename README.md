# Mobile-Games-AB-Testing
Cookie Cats is a hugely popular mobile puzzle game developed by Tactile Entertainment. It's a classic "connect three" style puzzle game where the player must connect tiles of the same color in order to clear the board and win the level. It also features singing cats.

As players progress through the game they will encounter gates that force them to wait some time before they can progress or make an in-app purchase. In this project, I analyze the result of an A/B test where the first gate in Cookie Cats was moved from level 30 to level 40. In particular, I analyze the impact on player retention.

## Table of Contents
- [Motivation](#motivation)
- [Overview](#overview)
- [Dataset](#dataset)
- [Steps](#steps)
- [Results](#results)
- [Dependencies](#dependencies)
- [License](#license)
- [Contact](#contact)


## Motivation
The global video game industry generated an impressive $150 billion in revenue in 2021, with mobile games accounting for approximately 51% of this figure<sup>[1]</sup>. While my gaming journey began with Spider-Man 2 on the PS2 in 2006, I've witnessed the undeniable surge of mobile gaming.

Though I'm deeply fond of immersive console experiences, the potential in mobile gaming is palpable. Retention stands out as a pivotal metric for any game, directly influencing purchases and referrals. Thus, it's paramount for mobile game developers to rigorously assess strategies to enhance retention, enriching both player experience and their revenue.

## Overview
As players progress through the levels of the game, they will occasionally encounter gates that force them to wait a non-trivial amount of time or make an in-app purchase to progress. In addition to driving in-app purchases, these gates serve the important purpose of giving players an enforced break from playing the game, hopefully resulting in that the player's enjoyment of the game being increased and prolonged.

But where should the gates be placed? Initially the first gate was placed at level 30, but in this notebook we're going to analyze an AB-test where we moved the first gate in Cookie Cats from level 30 to level 40. In particular, we will look at the impact on player retention. But before we get to that, a key step before undertaking any analysis is understanding the data.

## Dataset

The data we have is from 90,189 players who installed the game while the AB-test was running. The variables are:

- userid: A unique number that identifies each player.
- version: Whether the player was put in the control group (gate_30 - a gate at level 30) or the group with the moved gate (gate_40 - a gate at level 40).
- sum_gamerounds: the number of game rounds played by the player during the first 14 days after installation.
- retention_1: Did the player come back and play 1 day after installing?
- retention_7: Did the player come back and play 7 days after installing?

When a player installed the game, they were randomly assigned to either.

## Steps

## Results

## Dependencies

## License

## Contact

### Sources
[1] Curry, D. (2023). _Mobile Games Revenue Data (2023)_. Business of Apps. [Link](https://www.businessofapps.com/data/mobile-games-revenue/#:~:text=Even%20though%20mobile%20games%20still,of%20all%20revenue%20in%202021.)
