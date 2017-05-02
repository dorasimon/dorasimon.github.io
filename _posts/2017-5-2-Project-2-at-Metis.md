---
layout: post
title: Project 2 at Metis
---
For this project I worked on predicting US movies' box office in China.

I scraped movie data from boxofficemojo.com, both China data and US data, then I inner joined them, resulting in a list of
movies that were released in both countries. (I didn't further filter it so it includes Chinese movies that were later released
in the US.)

With most of the features being categorical variables, I created dummy variables for them, such as Rating, Genre, Distributor.
I also added two columns: Sequel and Academy Award.

First, I used OLS model with all the original features. R^2 was 0.49. So I looked at the p value and got rid of the ones whose
p value was really high, and only kept US Gross, Rating Score, Drama, Medium Distributor. Then I ran OLS again. R^2 rocketed to
0.98.

Then, I used those four features to run Lasso, Ridge, RidgeCV=10, ElacticNet, Random Forest... Among which Random Forest
returned the best result at over 0.4. There are many other features that I could have included, such as Director, Actor/Actress,
Release Time Difference... but due to time limit I was not able to scrape those, which supposely would contribute to the model
considerably.
