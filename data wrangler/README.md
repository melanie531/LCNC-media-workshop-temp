# Music Recommendation

## Overview
Amazon SageMaker helps data scientists and developers to prepare, build, train, and deploy machine learning models quickly by bringing together a broad set of purpose-built capabilities. In this demo, learn about how SageMaker can accelerate machine learning development by way of an example where we build the perfect musical playlist tailored to a user's tastes.

## Dataset
Example track (track.csv) and user ratings (ratings.csv) data is provided on a publicly available S3 bucket found here: **s3://sagemaker-sample-files/datasets/tabular/synthetic-music**
We'll be running a notebook to download the data in the demo so no need to manually download it from here just yet.

**tracks.csv**  
- trackId: unique identifier for each song/track 
- length: song length in seconds (numerical)
- energy: (numerical)
- acousticness: (numerical)
- valence: (numerical)
- speechiness: (numerical)
- instrumentalness: (numerical)
- liveness: (numerical)
- tempo: (numerical)
- genre: (categorical) 

**ratings.csv**  
- ratingEventId: unique identifier for each rating 
- ts: timestamp of rating event (datetime in seconds since 1970)
- userId: unique id for each user
- trackId: unique id for each song/track
- sessionId: unique id for the user's session
- Rating: user's rating of song on scale from 1 to 5

For this workshop, we'll be using our own generated track and user ratings data, but publicly available datasets/apis such as the [Million Song Dataset](http://millionsongdataset.com/) and open-source song ratings APIs are available for personal research purposes. 
