# NHL Game Group Project -- INSY695 Enterprise DS & ML In Production I
**Team No.**: 5509-0, Group 9 \
**Team Name**: NHL Pros \
**Product Manager**: Anqi Chen (angelach99) \
**Business Analyst**: Matthew Buttler Ives (matt-buttlerives) \
**Data Analyst**: Mesaye Baahiru (mesaye3), kexin Chen (KEX9027), Rebecca Mukena Yumba (beccarem) \
**Data Scientist**: Betty Au (bettyau), Claire Cai (clairecai97) 

## Overview and Business implication



## Data 

The data source is from: 
[NHL Kaggle Dataset](https://www.kaggle.com/martinellis/nhl-game-data?select=game.csv )

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

The combined dataset after Data Merging step is [period1_combined.csv](https://github.com/McGill-MMA-EnterpriseAnalytics/NHL-Game/blob/main/Preprocessed%20Data/period1_combined.csv), and the cleaned dataset after Data Pre-processing step is [readyformodel_V2.csv](https://github.com/McGill-MMA-EnterpriseAnalytics/NHL-Game/blob/main/Preprocessed%20Data/readyformodel_V2.csv).

## Tutorial
- Data Merging: [project_EDA_vs.ipynb](https://github.com/McGill-MMA-EnterpriseAnalytics/NHL-Game/blob/main/project_EDA_v2.ipynb)
- Data Exploration: [Data Exploration_V2.ipynb](https://github.com/McGill-MMA-EnterpriseAnalytics/NHL-Game/blob/main/Data%20Exploration_V2.ipynb)
- Data Pre-processing: [Data Imputation, Encoding,Cleanup,Feature Importance_V2.ipynb](https://github.com/McGill-MMA-EnterpriseAnalytics/NHL-Game/blob/main/Data%20Imputation%2C%20Encoding%2CCleanup%2CFeature%20Importance_V2.ipynb)
- Modeling: [NHL-Modeling_v2.ipynb](https://github.com/McGill-MMA-EnterpriseAnalytics/NHL-Game/blob/main/NHL-Modeling_v2.ipynb)
- Causal Inference: [NHL_Causal_Inference.ipynb](https://github.com/McGill-MMA-EnterpriseAnalytics/NHL-Game/blob/main/NHL_Causal_Inference.ipynb)
- Clustering:
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


## Acknowledgements
This project was conducted as part of the final group project for INSY695: Enterprise DS & ML In Production I, Winter 2022, with Instructor Fatih Nayebi at Desautels Faculty of Management, McGill University. 
