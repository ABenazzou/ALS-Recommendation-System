# Movie Recommendation System using PySpark and Collaborative Filtering

## Overview

This repository contains code for building a movie recommendation system using PySpark and the Collaborative Filtering technique. The system uses the MovieLens 100k dataset for movie ratings and user data.

The code sets up a PySpark environment, loads the dataset, and trains an ALS (Alternating Least Squares) recommendation model. It also explores different approaches, including occupation-based recommendations and movies-genres based recommendations.

## Table of Contents

- [Setup](#setup)
- [Loading and Preprocessing Data](#loading-and-preprocessing-data)
- [Initial ALS Model](#initial-als-model)
- [Exploring Movies Datasets](#exploring-movies-datasets)
- [Checking out Joins between Users and Movies](#checking-out-joins-between-users-and-movies)
- [Occupations-Based Approach](#occupations-based-approach)
- [Exploring Cosine Similarity Based on Movies Genres](#exploring-cosine-similarity-based-on-movies-genres)
- [Movies Ratings Based Cosine Similarity](#movies-ratings-based-cosine-similarity)
- [ALS Model with Initial Filled DF](#als-model-with-initial-filled-df)
- [Recursively Filling All Possible Similarities](#recursively-filling-all-possible-similarities)
- [Final ALS Model](#final-als-model)

## Setup

To set up the PySpark environment, make sure to follow the installation steps for PySpark and related dependencies. The code is designed to run on Google Colab, and you will need a Google Drive account to access and load the dataset.

## Loading and Preprocessing Data

The code begins by loading the MovieLens 100k dataset, including user ratings, movie data, and user data. It preprocesses the data for further analysis and model training.
Our movies data is composed mainly of 3 parts:

- Users datasets: user related information (age, name, occupation …)
- Movies dataset: movies related information (name, release date, genres …)
- Ratings dataset: the rating that each user gave for a specific movie.


## Initial ALS Model

The initial ALS model is trained using the ratings data. The code explores different model parameters and evaluates the model's performance.

## Exploring Movies Datasets

This section focuses on exploring the movies dataset, including movie names, release dates, and genres. It preprocesses this data for future recommendations.

## Checking out Joins between Users and Movies

Here, the code performs various joins between user data, movie data, and ratings data. It explores different approaches, including occupation-based recommendations.

## Occupations-Based Approach

The code implements an occupation-based approach to recommend movies to users with the same occupation. It calculates the mean of ratings for users with the same occupation and assigns those mean values to movies not previously rated by those users.

## Exploring Cosine Similarity Based on Movies Genres

The code calculates cosine similarity between movies based on their genres. However, this approach has limitations, as it might recommend too many similar movies.

## Movies Ratings Based Cosine Similarity

To address the issues with genre-based similarity, the code calculates cosine similarity based on movie ratings. It creates a user-movie matrix and uses cosine similarity to find the closest users for filling missing ratings.
let’s consider user A 
ratings, and compare them to user B ratings for each movie they rated. If they are close, then user B and 
user A probably likes the same type of movies, hence we can recommend each other’s movies.

|       | Movie 1 | Movie 2 | Movie 3 |
|-------|---------|---------|---------|
| User 1|   5     |    X    |   3     |
| User 2|   5     |    2    |    X    |
| User 3|   2     |    5    |    X    |

For instance, in the above table we will assign 2 as rating for the Movie 2 on User 1 while assigning 3 to 
Movie 3 on User 2, this will help us fill a little bit more the initial matrix as discussed during the course.
The above approach followed by ALS with some parameters tuning resulting in a RMSE of 0.84 instead of 
the usual 0.92.

## ALS Model with Initial Filled DF

The final ALS model uses the user-movie matrix with missing ratings filled based on cosine similarity. It trains the model with the filled data and evaluates its performance.

## Recursively Filling All Possible Similarities

This section shows how the code recursively fills all possible similarities in the user-movie matrix until no further improvements are possible.

## Final ALS Model

The final ALS model is trained with the fully filled user-movie matrix. It includes model parameters and performance evaluation.

Feel free to explore the code and adapt it for your movie recommendation project.

