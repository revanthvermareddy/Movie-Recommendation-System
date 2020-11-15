## Table of contents
* [General info](#general-info)
* [Recommendation System](#recommendation-system)
* [Types](#types)
* [Assumptions](#assumptions)
* [Approach](#approach)
* [Steps](#steps)
* [Regularization](#regularization)
* [Rmse](#rmse)
* [Why vectors to hold data?](#why-vectors-to-hold-data)
* [Technologies](#technologies)
* [Setup](#setup)

## General info
This project is a movie recommendation system which uses machine learning to recommend the user a movie to watch, either by analyzing the user's preferrence based on his previous ratings/reviews or by picking the most liked one among others

## Recommendation System
A computer program that helps user discover products or content by predecting the user's rating of each item and then showing them the items they would rate highly

## Types
1. Content-based recommendation systems - uses knowlwdge about each product to recommend new products (works even when the product has no user reviews)
2. Collaborative-filtering recommendation systems - making recommendations only based on how users rated products in the past (doesn't require any knowledge about the products themselves but need the user reviews already available)

## Assumptions
Though each and every user is unique and would give a different rating than what we expect. Here we go with the tacit assumption that user ratings are a reflection of how much a movie appeal's to that user's unique set of interests

## Approach
We use the already available sparse matrix of RATINGS (= USERS x MOVIES) and then reverse factrorize it to get USERS and MOVIES matrices so that they best fit the already available ratings. We then multiply the obtained USERS and MOVIES matrices to get the unknown ratings of a movie, finally recommend movies in the order of most highly rateable for each user.

Though this seems to be straight forward, we should note that we directly cannot use sparse matrix as most of the data points are missing. Hence we'll instead use iterative approach where in we first pick random values for both USERS, MOVIES matrices and then try to modify those values to match the results with those of the available values in sparse matrix.

## Steps
1. Set all elements in USERS and MOVIES to random numbers. Right now USERS x MOVIES will result in random numbers.
2. Create a "Cost function" that checks how far off USERS x MOVIES currently is from equaling the known values of the RATINGS matrix.
3. Using a numerical optimization algorithm, tweak the numbers in USERS and MOVIES a little at a time. The goal is to get the ost function a little closer to zero. We'll use SciPy's 'fmin_cg()' optimization function to find the minimum cost.
4. Repeat step 3 until we cannot reduce the cost function further. The USERS and MOVIES matrix values we find will be estimates. [USERS x MOVIES ~ RATINGS]

We use low_rank_matrix_factorization approach for this and is available as a utility in matrix_factorization_utilities.py file

## Regularization
A control in the model that limits how much weight to place on one single attribute when modeling users and products. The higher the regularization amount, the less weight we can put on any single attribute. For larger dataset use larg value(1.0, 10.0, etc) and for smaller dataset use small value(0.1, etc). Finding the right value takes experimentation

## RMSE
RMSE (Root-Mean-Square Error) is a measurement of the difference between the user's real rating and the rating we predicted. The lower the RMSE, the more accurate the model is.

## Why vectors to hold data?
To support CPU's single instruction multiple data (SIMD) operations
	
## Technologies
Project is created with:
* Python version: 3.7
	
## Setup
To run this project, install it locally using pip:

```
$ cd ../Movie_Recommendation_System
$ pip install -r requirements.txt
$ python make_recommendations.py
```