## Intro

What makes a good RPG game appealing to a gamer? What did gamers enjoy and dislike the most in other game genres on the Xbox One, Playstation 4 and Nintendo Switch consoles? With the next generation version of these consoles on the rise, in this project I aimed to conduct sentiment analysis on user reviews and considered two business cases were the model may be useful. Exploratory data analysis revealed the most predictive words of positive and negative reviews in different game genres.

The best performing model was a Logistic Regression model, achieving an ROC-AUC score of around 92%. The model was optimized differently for two business cases. The first was if a company wanted to assess a general response to a release by customers on social media. For this case the metric of interest was balanced accuracy. With a threshold of 0.54 the highest balance accuracy of 84.3% was attained. Allowing game developers to accurately assess their games versus their competitors or to evaluate how consumers receive their game.
The second business case consisted of helping companies find potential influencers on social media that were willing to promote or advertise the product. For this case the F score was adjusted to favor precision with a beta = 0.25. With the adjusted F score and a threshold of 0.75 the model achieved a precision of about 95%, making the model an efficient predictor of positive reviews greatly reducing the number of false positives.

_The full report can be found in the notebooks folder_


## Context

With the next generation gaming consoles of Microsoft’s Xbox Series X and Sony’s Playstation 5 recently being released, I reflected on some of the games I enjoyed the most on their predecessors and the Nintendo Switch. Some of my favorite titles included The Witcher 3: Wild Hunt, Borderlands, Kingdom Hearts series and the Dishonored series. If you are not familiar with game genres all of my favorite titles are considered role playing games (RPG) and action adventure games. 

Personally, the aspects I enjoyed about these games was the versatility a player is given to customize and equip their character with different skills and armor, the open world environment and the mystical and fantasy-like characteristics of these games. I wanted to see what other gamers thought about these games and games in other genres. I decided I could perform sentiment analysis on game reviews submitted by the average gamer and not critics to get a sense of what the public actually felt.


## The Data

The data was scraped off Metacritic, a website where people review movies, music, video games and other types of media. For this project 15 reviews were scraped for all game titles across the Xbox One, PS4 and Switch for games with at least 15 reviews. The features scraped included:
* title: 				Title of the game
* platform: 			Console reviewer played the game on
* metascore: 			Average score given to the game by various game critics 
* metasentiment: 		Overall critic sentiment classification
* average_userscore: 		Average score given to the game by users
* average_usersentiment: 	Overall user sentiment classification
* developer: 			Developer of game
* genre: 				Genre of game
* number_of_players: 		Number of players that can play the game
* esrb_rating: 			Entertainment Software Rating Board (ESRB) rating
* release_date:			Release date of game
* username: 			Metacritic username of the game reviewer
* userscore: 			Individual user rating
* usersentiment: 		Individual user sentiment classification
* review: 			Text review left by user
* review_date: 			Date review was left by user

There were various rows with missing values for various features but as these rows all contained the null values and only accounted for 2% percent of the data, they were dropped. The only feature with a significant amount of missing values was the ‘number_of_players’ columns. About 16% of the data did not have a value assigned to this feature.

To address the null values in the ‘number_of_players’ column, the titles for the games having a null value were explored. There were a mixture of singleplayer and multiplayer games missing values for the number of players. Each title was googled to see if the game was a single or multiplayer game. Then, to reduce the amount of different, unnecessary amounts of values for the ‘number_of_players’ columns of the dataframe, the game titles for ‘No Online Multiplayer’ games were also explored. Mostly all, if not all were single player games. For simplicity, the ‘number_of_players’ column was then converted to a binary column where a game was either considered a single player game (values of ‘No Online Multiplayer’ and ‘1 Player’) or multiplayer game (all other values).

Using the lang_detect library each review was tagged with an abbreviation of the language it was written in. Different review density features were created for EDA and to potentially be used for modeling such as part of speech counts, word counts, sentence counts, punctuation counts, etc. Finally, the reviews were cleaned in the following order:
1. Transformed into lower case
2. Stripped of digits
3. Expanded contractions
4. Emojis transformed into words
5. Stripped of punctuation
6. Stripped of white space
7. Filtered from stop words
8. Lemmatized

## Exploratory Data Analysis

### _How are the user review scores distributed in the data?_


Figure 1: Distribution of user scores

Metacritic classifies a review as positive, mixed and negative by the user’s score. User scores range from 0 - 10. The following ranges distinguish the user’s sentiment:
Positive:	7.5 -10
Mixed:		5 - 7.49
Negative:	0 - 4.99

Most of the reviews in the dataset were positive, accounting for about 57% of the total reviews shown in Fig. 1. A whopping 10% of all reviews received a 0. It seems like people tend to enjoy video games released on console or they tend to be easily pleased with the attributes game developers add to their games.


### _Are positive user reviews longer than negative ones?_

Figure 2: Variability of word counts in reviews by user sentiment

On average reviews where the user had mixed feelings about a game, encompass the most words among all reviews (Fig. 2). This could be due to the gamer expressing what he enjoyed in the game and what he disliked. With more words a reviewer with mixed feelings toward a game can vividly express why they experienced conflicting emotions. 

There was a statistically significant difference among positive and negative reviews (p-value < 0.001). Positive reviews were generally the shortest type of reviews with the average positive review having somewhere between 70 and 90 words. The negative reviews may have been written in similar fashion. Perhaps accounting for the larger number of word usage from positive reviews, with additional excerpts explaining how the game could be improved.

__Positive Example:__ _“A definitive release was not necessarily needed but extremely welcomed. The added content made an already flawless game better. Playing through the game a second time was somehow more fun. I will always highly recommend this game. The best side scrolling game Xbox One currently has to offer. Beautiful graphics, fluid controls and solid game play that almost forces you to finish in one sitting it's so riveting.”_

*Median word count = 69


__Negative Example:__ _“It's not a bad game but the gameplay is an outdated one. It by no means a 10 out of 10: - "Realism" is annoying. I hate watching Ioot, skin and cook animations 100 times. -  Parking a horse or picking up something is frustrating as you have to stand in the exact right position to do so. -  75% of the game time it takes riding to the destination to play the game a bit. -  The cover system, menu system and controls are retrograde”_

*Median word count = 79


### _What are the most predictive words in game reviews by genre and sentiment?_
(Put pic of word cloud and short description)

## Modeling

## Business Case 1

## Business Case 2
