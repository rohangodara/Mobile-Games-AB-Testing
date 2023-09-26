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
1. Validating Database:
We notice that there are roughly the same number of players in each version group (gate_30 and gate_40). This allows us to proceed without sampling at this moment.
2. Create Null Hypothesis: Game version has no effect on day 1 and day 7 retention.
3. Create Alternate Hypothesis: Game version does have an effect on day 1 and day 7 retention.
4. Bootstrap day 1 mean retention to find density functions of each group. We notice that there is a trend where gate_30 has a higher bootstrapped mean retention. (NOTE: We bootstrap to build certainty that our initial finding of gate_30 having higher retentions is not just based on chance)
5. Utilize above bootstrap to plot density function of % difference in mean retention.
6. Identify probability that gate_30 has a higher day 1 retention than gate_40. This probability came out to ~0.9!
7. Repeat the same steps for Day 7 retention.
8. Conclude that the alternate hypothesis is correct.

## Results
We notice from our data that players assigned to the Gate 30 group have a higher mean day 1 retention. To be confident, we bootstrap our data 500 times and create the following density functions showing this difference. \
![ab both](https://github.com/rohangodara/Mobile-Games-AB-Testing/assets/77946323/ee54fcf0-c3d3-4bc8-bfe3-be638f04beba)
![ab middle](https://github.com/rohangodara/Mobile-Games-AB-Testing/assets/77946323/252f31e6-5237-4d5f-97ad-61d6838af654) \
We find that for the day 1 retention, players who are assigned to Gate 30 have a 0.962 probability of having a higher retention. \
This is a significant difference! But, it is also possible that some players haven't reached the gate yet so it is important to check the Day 7 retention as well. We repeat the same steps as above to find our density functions for the percentage difference in Day 7 retention between the two groups. \
![ab last](https://github.com/rohangodara/Mobile-Games-AB-Testing/assets/77946323/9f4d2b25-caed-4e55-ab89-46c95e784af1) \
The percentage difference not only stays consistent with direction, but increases in magnitude. \ 
Hence we can report that forcing players to wait an arbitrary amount of time at gate 30 as opposed to gate 40 improves player retention for Cookie Cats. But why is this? The theory of hedonic adaptation can give one explanation for this. In short, hedonic adaptation is the tendency for people to get less and less enjoyment out of a fun activity over time if that activity is undertaken continuously. By forcing players to take a break when they reach a gate, their enjoyment of the game is prolonged. But when the gate is moved to level 40, fewer players make it far enough, and they are more likely to quit the game because they simply got bored of it.

## Dependencies
- Pandas
- Matplotlib

## License
This dataset is provided by DataCamp and the good folks over at Cookie Cats. Thank you to them!

## Contact
- Phone: 415-694-0512
- Email: rohan.godara00@gmail.com

### Sources
[1] Curry, D. (2023). _Mobile Games Revenue Data (2023)_. Business of Apps. [Link](https://www.businessofapps.com/data/mobile-games-revenue/#:~:text=Even%20though%20mobile%20games%20still,of%20all%20revenue%20in%202021.)
