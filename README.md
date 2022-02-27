# NHL Game Group Project -- INSY695 Enterprise DS & ML In Production I

**Team No.**: 5509-0, Group 9 \
**Team Name**: NHL Pros \
**Product Manager**: Anqi Chen (angelach99) \
**Business Analyst**: Matthew Buttler Ives (matt-buttlerives) \
**Data Analyst**: Mesaye Bahiru (mesaye3), kexin Chen (KEX9027), Rebecca Mukena Yumba (beccarem) \
**Data Scientist**: Betty Au (bettyau), Claire Cai (clairecai97) 

## Overview and Business implication
Can we construct a classification model that can predict which National Hockey League **(NHL)** hockey team will win a game? This repository seeks to answer that question. By applying various supervised and unsupervised machine learning models and using public datasets offered through Kaggle, our team has constructed a classification model which predicts the outcome of a hockey game during a regular season using only statistics captured in the first period of play. The purpose of this project is to add our insights to the growing field of sports betting and to challenge ourselves as aspiring professionals in the field of analytics to solve a notoriously difficult prediction problem. 

From professional sports teams to passionate fans, data scientists and analytics experts have tried to predict the outcome of sport games using a variety of different approaches, assumptions and statistics. Some analysts use data as far back as 1919 in order to gain further insights. Predicting the outcome of a game is used in a variety of sports such as the NHL, National Football League, (NFL) and the National Basketball Assocation (NBA). While simple in theory, developing a predictive model for classifying which team would win or lose has proven to be one of the most challenging forms of modeling in data science. Often, accuracy levels for this type of modeling range from 50-70%. Even models with accuracy higher than 70% typically only perform well for one season. Currently, one of the best models used in the NHL sports betting field is named **Forecheck** which offers a 62% accuracy. (If you are interested to read more, here is an article by **The Globe And Mail** that discusses Forecheck: https://www.theglobeandmail.com/sports/hockey/nhl-predictions-hockey-methodology/article37603494/) 

The primary purpose of prediction in the field of sports analytics for those not employed by the NHL is sports betting. Retail sports analysts create predictive model’s that are used to inform their decision making when betting on hockey teams. The objective is to build a model that performs better than “gut instinct” and offers the potential to beat the Sports Bookies (more on that later). 

Listed below are some of the most important types of Sports Betting: 

- **Moneyline**: Moneyline betting is the most popular form of sports betting in hockey. Simply, players bet on which team will win the game. The reason Moneyline is popular in hockey is due to the frequent low number of goals for most games and is based on the existing likelihood for each team to win. So when you bet on a team to win the game, you are betting on the Moneyline.  

- **Over and Under**: This unique form of betting focuses on the total number of goals scored in a game by both teams. Bettors can place bets on if the total amount of goals scored during the game will be above or below a certain threshold set by Sports Bookies. If the total amount is “Over” or “Under” that threshold, a bettor will profit if they managed to pick correctly.  

- **Puck line**: Puck line betting focus on the difference between the number of goals scored in a game by both teams, also known as the spread. First each team is assigned as the underdogs or the favourites. This label will give each team either +1.5 points or –1.5 points. A bettor can place a bet on either team, or both, and then that team must either win or lose the game by that certain number of goals (points) for the bettor to profit. This kind of bet is meant to balance the games between stronger and weaker teams.  

For each betting method, all teams are given a set of odds that can be expressed as negative or positive indicating if a team is considered the underdog or the favourite. Sportbookies determine these odds, also known as the spreads between teams based on the number of bets taken throughout the week on both teams and will change the point spread to reflect the belief by the bettors on which team will win. They may also artificially change the point spread to maintain interest of bettors on the game. 

For our team’s use case, we decided to build a model that would be useful for **live/In-game Moneyline** betting as this type of Sports betting often tends to be the most dynamic with more bettor participation and whose implications offer the largest contribution to the field of sports betting and predictive modeling. The proof of value (PoV) for our use case revolves around our model’s accuracy. Is the performance of our model valuable to the sports betting community? To answer this question, we must use the measure of value that begins at 52.4%. In the field of sports betting, an accuracy of 52.4% of picking which team will win is needed to breakeven; covering a bettor's losses along with fees associated with the bets. Any bettor whose accuracy is above 52.4% will see some profit. But an accuracy of 53% is where real money can be made and is the benchmark for a model to be considered as a “good model”. Therefore, our team’s objective is to make sure our model’s accuracy either reach’s or goes beyond 53%.  


## Data 

The data source is from: 
[NHL Kaggle Dataset](https://www.kaggle.com/martinellis/nhl-game-data?select=game.csv )

The tables we used are:
- game.csv
- game_plays.csv
- game_teams_stats.csv
- game_skater_stats.csv
- game_goalie_stats.csv
- player_info.csv

Here are the definitions of features used for this project:
- 'game_id': Unique id of the game
- 'team_id': Unique id of the team
- 'HoA': Is the team at home or away?
- 'won': Did the team win the game?
- 'settled_in': Did the game end in regular time or in overtime.
- 'head_coach': Head coach
- 'goals': Number of goals
- 'shots': Number of shots
- 'hits': Number of hits
- 'pim': Number of Penalty Infraction Minutes
- 'powerPlayOpportunities': Number of Power Play Opportunities
- 'powerPlayGoals': Number of Power Play Goals
- 'faceOffWinPercentage': Percentage of Face Off Wins
- 'giveaways': Number of Giveaways
- 'takeaways': Number of Takeaways
- 'blocked': Number of Blocks
- 'startRinkSide': Starting Rink Side
- 'type': Type of Game
- 'date_time_GMT': Time of the Game
- 'home_rink_side_start': Side of the Rink where the Home team starts
- 'venue': Venue
- 'venue_time_zone_id': Id Time Zone of the Venue
- 'venue_time_zone_offset': Offset of Time Zone of the Venue
- 'venue_time_zone_tz': Time Zone of the Venue
- 'timeOnIce': A players total time on the ice
- 'evenTimeOnIce': When a team has the same number of players on the ice as the opposing team
- 'shortHandedTimeOnIce': When a team has less players on the ice than the opposing team
- 'powerPlayTimeOnIce': Average Power Play Time on Ice
- 'goalie_replacement': Was the goalie replaced?

The combined dataset after Data Merging step is [period1_combined.csv](https://github.com/McGill-MMA-EnterpriseAnalytics/NHL-Game/blob/main/Preprocessed%20Data/period1_combined.csv), and the cleaned dataset after Data Preprocessing step is [readyformodel_V2.1.csv](https://github.com/McGill-MMA-EnterpriseAnalytics/NHL-Game/blob/main/readyformodel_V2.1.csv).

## Tutorial
Please notice that there could be documents of previous versions. Here are the links for documents of final versions.
- Data Merging: [project_EDA_vs.ipynb](https://github.com/McGill-MMA-EnterpriseAnalytics/NHL-Game/blob/main/project_EDA_v2.ipynb) and [New Dataset Revised for Period #1.ipynb](https://github.com/McGill-MMA-EnterpriseAnalytics/NHL-Game/blob/main/New%20Dataset%20Revised%20for%20Period%20%231.ipynb)
- Data Exploration: [Data Exploration_V2.ipynb](https://github.com/McGill-MMA-EnterpriseAnalytics/NHL-Game/blob/main/Data%20Exploration_V2.ipynb)
- Data Preprocessing: [Data Preprocessing_V2.ipynb](https://github.com/McGill-MMA-EnterpriseAnalytics/NHL-Game/blob/main/Data%20Preprocessing_V2.ipynb)
- Modeling: [NHL-Modeling_v2.ipynb](https://github.com/McGill-MMA-EnterpriseAnalytics/NHL-Game/blob/main/NHL-Modeling_v2.ipynb)
- Causal Inference: [NHL_Causal_Inference.ipynb](https://github.com/McGill-MMA-EnterpriseAnalytics/NHL-Game/blob/main/NHL_Causal_Inference.ipynb)
- Clustering: [Clustering Approach.ipynb](https://github.com/McGill-MMA-EnterpriseAnalytics/NHL-Game/blob/main/Clustering%20Approach.ipynb)
- Presentation Slides: [Group 9 Presentation Slides.pdf](https://github.com/McGill-MMA-EnterpriseAnalytics/NHL-Game/blob/main/Group%209%20Presentation%20Slides.pdf)


## Modelling Result Analysis
We display the visualization of validation result, roc auc score, classification report and confusion matrix for 4 models respectively by using the function ```clf_score```. The visualization is more intuitive than numbers to show the results of cross-validation. Based on the output above, we can conclude that ```Random Forest``` generates the highest number of correct predictions regarding the game's outcome. The most contributing factors are outlined below:  
* ```goals``` 
* ```timeOnIce``` 
* ```shortHandedTimeOnIce``` 
* ```powerPlayTimeOnIce```
 
Based on cross validation of the Random Forest model, the accuracy score improves from 0.8438 to 0.8465 after the hyperparameters have been tuned. The detailed process is showed in Section 5.4.  

In Section 5.4, you can see that we choose to tune the hyperparameters: 
* ```max_features``` 
* ```n_estimators``` 
* ```min_samples_leaf``` 
* ```random_state``` 

The modeling output implies that decision-makers should focus on the top contributing factors such as number of goals, time on ice, number of shots handled on ice, power-play time on ice when judging the outcome of the hockey game with the first-period statistics. By leveraging the Random Forest model, users can utilize hockey game statistics to determine the game’s outcomes as to which team will win or lose after the first period. The model generates accurate predictions on sports betting over randomly guessing the outcome. Also, the model performance validates the proof of value and achieves the business objective to develop a predictive model with an accuracy score higher than 52.4% in order to break even.  

The system limitation is that Sports analytics is generally difficult to model with the best models performing at accuracy levels ranging from 50-70%. However, our model performs very well at the accuracy level of around 84%, which potentially faces overfitting issues. Our team will carry over investigating this topic in the second half of the course. 

## Causal Inference Result Analysis
For the causal inference analysis, the objective is to examine the difference between the outcome of the game between the treatment and control group. The outcome is a binary variable, which is to win or lose the game. The explanatory variables are a list of 22 numerical variables of game statistics for period 1. And the treatment here is the whether the team is home or away. It is understandable that this might not be a very suitable treatment in this case, which is due to data limitation. But for this project, this variable will be used as an example to demonstrate the difference in outcome of the game for groups who play at home and not at home.  

From various causal inference models, time on ice is the most important feature, following Number of Penalty Infraction Minutes and goals. From the Uplift tree and random forest classifier algorithms, time on ice and power play time on ice are the top two most important features. According to the average treatment effect score, teams who play games away will have greater chance to win the game compared to teams who play games at home. 

Overall, time on ice and number of penalty infraction minutes are significant factors that could impact the outcome of the game. And whether the team will play at home or away do cause a difference in the outcome. In future studies, alternative treatment variables such as a certain nutrition that athletes take, or the use of a new hockey equipment could be used for causal analysis. These factors could create an impact on the outcome and having results of such could provide critical judgements for hockey betting. 

## Clustering Result Analysis
For the clustering analysis, we ran a KMeans algorithm with 2 clusters (winning vs losing team). Overall there are very few differences on average between winning teams and losing teams, a few notable ones are:
- On the winning teams the power play scores more with less time on ice in average.
- The winning teams are more often at home
- The winning teams have much less goalie replacements than the losing teams
Other aspects of the game such as average time on ice, penalties and start rink side, are the same for all teams whether they win or lose.

The silhouette score confirms that the differences between the clusters are not well defined and that makes our recommendations from this analysis non-actionable. <br/>

## Acknowledgements
This project was conducted as part of the final group project for INSY695: Enterprise DS & ML In Production I, Winter 2022, with Instructor Fatih Nayebi at Desautels Faculty of Management, McGill University. 
