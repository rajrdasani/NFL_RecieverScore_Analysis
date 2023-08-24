# NFL WR Catch Analysis

Inspiration:
- FiveThirtyEight's Best NFL Receivers Analysis [https://projects.fivethirtyeight.com/nfl-receiver-rankings/]
  
- Seth Welder's Video on Best Catch Scores in the League [https://www.youtube.com/watch?v=veMsKHA72sU&ab_channel=NFLonESPN]

Goal:
Predict WR Catch Scores based on their previous seasons

Inspired by the work by @Seth Welder and @FiveThirtyEight on Reciever Score, looking at advanced stats to find the best NFL Receivers, I looked to see if I could predict these scores for the following season based on previous years stats via Regressions and Clustering ML models, and identified 4 breakouts:

“Rebounders”: Gabe Davis, Marquez Valdes-Scantling
“Ascenders”: Alec Pierce, Romeo Doubs

I first looked at looking at which WRs had the biggest deltas between 2021 and 2022, and found that players who have a high score keep consistent catch scores, unless a player deals with injury (Andrews, Kupp) or situations changed and they became more of a primary weapon on their team, limiting their catch ability (Adams, Kirk)

[CatchScore_2021v2022.png]

I also looked at players who had the biggest jump out of any of the years available (2017-2022) and found a lot of top WRs here either had an amazing season, and then had a drastic fall in WR score in following years (Antonio Brown, Julio Jones, Michael Thomas); or had a great season compared to their rookie years (Amari Cooper, Zay Jones). Additionally, there were a lot of TEs here, where opportunity and involvement in the pass game was more of a clear factor.

[BiggestCatchScoreDelta_2017_2022.png]

Then I created a linear regression model, which ended up being the best model via RMSE, with a weak R**2 of 0.33, as it was able to predict the stability of many WRs well, and even the regression back to the mean for some players (Jakobi Meyes 2020-21).

[LinearRegression_Year1Predictions.png]

I then ended up creating a variety of clustering algorithms, including a variety of Random Forests and Regression Trees, all showing similar or slightly worse predictions as the Linear Regression, all consistently missing the top breakouts. But they did inform that a player’s years stats, yards and open score were significant, but catch score and YAC score were not. 


So to predict breakouts, I used a K-means algorithm to find the key traits of these top breakouts. But rather than grouping them by the fact they were breakouts, I used a train/test procedure, and grouped WRs beforehand, and found which cluster had the highest delta in overall receiver score. 

[BreakoutCluster_Y0vY1Overalls.png]

Mapping this KMeans to the 2022 players, there were 24 breakouts that fit the mold, but I manually picked the ones that fit the trend of what we learned above, which were the following traits:
- young players with ambiguous roles in past years 
- an above average amount of yards (~600-700)
- low yards run (~400)
- extremely low catchscore (relative to their other scores)

Gabe Davis and Marquez Valdes-Scantling were both 2 of the biggest fallers in WR score from last year (more than a 20 point fall) for a variety of reasons. However players on top teams, with another year on their belt in the same offense, with slight changes to their offenses is a formula for them to make them a solid breakout candidate if things align. (Similar breakouts: Davante Adams 19-20, Tyler Lockett 20-21)

For Pierce and Doubs, the potential is limitless for these young WRs with new QBs. With changes bound to happen, these WRs who showed flashes in their first years can rise to the alpha WR in their offense. Watch for Pierce’s Catch Score and Doubs’s Open Score to rise to league average or above. (Similar Breakouts: Zay Jones 17-18, Cooper Kupp 20-21)
