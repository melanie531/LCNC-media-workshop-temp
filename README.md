# Music Recommendation

With the rapid growth of the commercial music streaming services, more and more people nowadayas are listening to music from they model devices. However, organising, managing and searching among all the digital music produced by the society is a very time-cosuming and tedious task. Using a music recommender system to predict the user's choices and suggest songs that is likely to be interesting has been a common practice used by the music providers.

<p align="center"><img width="500" height="500" src="./img/resize_AdobeStock_51102907.jpeg"></p>

## Overview
Amazon SageMaker helps data scientists and developers to prepare, build, train, and deploy machine learning models quickly by bringing together a broad set of purpose-built capabilities. In this workshop, learn about how SageMaker can accelerate machine learning development by way of an example where we build the musical playlist tailored to a user's tastes.

## Dataset

<div class="alert alert-block alert-info">
<b>Dataset</b>

The dataset is required before we begin, ensure that you have downloaded it by following the instructions below.

</div>

Example track (track.csv) and user ratings (ratings.csv) data is provided on a publicly available S3 bucket found here: **s3://sagemaker-sample-files/datasets/tabular/synthetic-music**
We'll be running a notebook to download the data in the demo so no need to manually download it from here just yet.

**tracks.csv**  

| **Column name**       | **Description**     | 
| :------------- | :---------- | 
|`trackId`| unique identifier for each song/track |
|`length`| song length in seconds (numerical)|
|`energy`| Energy is a measure from 0.0 to 1.0 and represents a perceptual measure of intensity and activity (numerical)|
|`acousticness`| A confidence measure from 0.0 to 1.0 of whether the track is acoustic. (numerical)|
|`valence`| A measure from 0.0 to 1.0 describing the musical positiveness conveyed by a track. (numerical)|
|`speechiness`| Speechiness detects the presence of spoken words in a track. (numerical)|
|`instrumentalness`| Predicts whether a track contains no vocals. (numerical)|
|`liveness`| Detects the presence of an audience in the recording. (numerical)|
|`tempo`| The overall estimated tempo of a track in beats per minute (BPM). (numerical)|
|`genre`| The genre of the song. For example, pop, rock etc. (categorical) |

**ratings.csv**  

| **Column name**       | **Description**     | 
| :------------- | :---------- | 
|`ratingEventId`| unique identifier for each rating |
|`ts`| timestamp of rating event (datetime in seconds since 1970)|
|`userId`| unique id for each user |
|`trackId`| unique id for each song/track |
|`sessionId`| unique id for the user's session |
|`Rating`| user's rating of song on scale from 1 to 5 |

For this workshop, we'll be using our own generated track and user ratings data, but publicly available datasets/apis such as the [Million Song Dataset](http://millionsongdataset.com/) and open-source song ratings APIs are available for personal research purposes. A full end-to-end pipeline can be found in this [SageMaker example](https://github.com/aws/amazon-sagemaker-examples/tree/main/end_to_end/music_recommendation).

## Experiment:

`SageMaker DataWrangler` for exploratory data analysis (EDA) of feature columns and joining different data sources.

`SageMaker Autopilot` to train and tune an optimal regression model.

## Pre-requisites:

  * We need to ensure dataset (loan default prediction) for ML is uploaded to a data source. 
  * Data source can be any one of the following options:
       * S3
       * Athena
       * RedShift
       * SnowFlake
       
       
<div class="alert alert-block alert-info">
<b>Data Source</b>

For this experiment the Data Source will be [Amazon S3](https://aws.amazon.com/s3/)

</div>


### Downloading the dataset, and notebooks

* Ensure that you have a working Amazon SageMaker Studio environment and that it has been updated. If you do not, follow the instructions [here](https://catalog.us-east-1.prod.workshops.aws/workshops/f560a788-af64-4e5a-a02c-a6c88516ab02/en-US/introduction/setup-sagemaker).
* Open an Amazon SageMaker Studio terminal to import the datasets and notebook into Amazon SageMaker Studio
    * Select **File / New / Terminal** from the menu at the top of Amazon SageMaker Studio.
    ![image](./img/dl_image-1.png)
