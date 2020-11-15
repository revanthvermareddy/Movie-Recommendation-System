## Table of contents
* [General info](#general-info)
* [Recommendation System](#recommendation-system)
* [Types](#types)
* [Technologies](#technologies)
* [Setup](#setup)

## General info
This project is a movie recommendation system which uses machine learning to recommend the user a movie to watch, either by analyzing the user's preferrence based on his previous ratings/reviews or by picking the most liked one among others

## Recommendation System
A computer program that helps user discover products or content by predecting the user's rating of each item and then showing them the items they would rate highly

## Types
1. Content-based recommendation systems - uses knowlwdge about each product to recommend new products (works even when the product has no user reviews)
2. Collaborative-filtering recommendation systems - making recommendations only based on how users rated products in the past (doesn't require any knowledge about the products themselves but need the user reviews already available)

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
$ python recommend.py
```