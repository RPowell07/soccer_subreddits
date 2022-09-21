# Project 3: Comparison of r/football and r/FIFA

#### Background:
Association football, aka soccer, is the world's most popular sport. In 1993, EA Sports developed Fifa, a yearly Association Football game which allows players to play as their favorite players on their favorite teams. Since then, Fifa has grown and it is now listed in Guinness World Records as the best-selling sports video game franchise in the world, having sold over 325 million copies as of 2021.[source](https://www.gamesindustry.biz/articles/2021-02-02-ea-extends-uefa-exclusivity-working-on-multiple-fifa-mobile-games) Every year, EA Sports releases a new version of Fifa, with Fifa 22 coming out last year. This Fall, Fifa 23 will be coming out, and will be the last Fifa, as EA Sports' partnership with Fifa will end after 30 years. Future games in the franchise will be named EA Sports FC.

For this project, we have pulled data from the website reddit, looking specifically at two subreddits: r/football, which is the main subreddit for association football, and r/FIFA, the main subreddit for the EA Sports FIFA video game franchise. In this notebook, we have put together a model for determining whether a post comes from the r/football or the r/FIFA subreddit.

#### Problem Statement:
As a data scientist for EA Sports, we want to examine what people are posting about in the r/football subreddit and compare that to what people are posting about in the r/FIFA subreddit in order to make recommendations on how to improve the game.

#### Datasets

* [`football_reddit_unclean.csv`](./data/football_reddit_unclean.csv): Data set of 2000 posts from r/Football 
* [`FIFA_reddit_unclean.csv`](./datasets/FIFA_reddit_unclean.csv): Data set of 2000 posts from r/FIFA 
* [`combined_reddit.csv`](./datasets/combined_reddit.csv): Combined, cleaned, data set of all posts in football and FIFA data sets (4000 posts)

#### Data Dictionary

| Feature | Type  | Description |
|------|------|--------|
|subreddit | category | which subreddit the post belonged to (1: r/football, 0: r/FIFA) |
|title | object | title of the post |
|author | object | author of the post |
|selftext | object | description of the post (if applicable) |
|cleantitle | object | title of the post without html characters and all lowercase |
|cleantext | object | description of the post (if applicable) without html characters and all lowercase |

#### Conclusions
Our best model was the Multinomial Naive Bayes using the CountVectorizer. We got an accuracy score of 89.8%. I chose this as our production model because the accuracy score was high, but also because both the training and testing scores were around 90%, so our model was good at predicting new data and did not appear to be overfit. Our recall score was 89.2% and our specificity was 90.4%. Because there is an equal negative between false positives and false negatives, I decided to go with the model with the best accuracy score.

The posts from r/football focus more on stats, with most common words including shots, passes, goals and time. Whereas the r/FIFA community is focused more on the players making up the team (most common words include players, player, play, team, and tots (team of the season)). This makes a lot of sense because the r/football community are all focused around the same leagues, where every individual FIFA player is focused on their own personal team and league rather than a league shared across all users.

My recommendation to EA Sports is to push their Competitive FIFA leagues (ePremier League, eMLS). A lot of the stats and keywords that are commonly found in the r/football community would be more prevalent in r/FIFA if there was a much smaller subset of leagues that was followed by the entire community.