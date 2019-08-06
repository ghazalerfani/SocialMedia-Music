# Sony Music Capstone.  Carnegie Mellon University, Heinz College, 2019.

This project reflects a 12 week capstone project completed as part of the MISM BIDA program at the Heinz College for Sony Music.  The purpose of this project was to identify how artists engaged with social media across various platforms and how their success might be measured on these platforms.

The team leveraged social media posts from 141 artists from Facebook, Instagram, Twitter, and Youtube.  Together with artist information from wikipedia and MusicBrainz, the team applied several machine learning models to identify underlying factors that contribute to social media engagement.

The following sections will outline the steps required to use and/or recreate these analyses.

## Prerequisites

This project relies heavily on the python programming language.  We used the Anaconda Distribution platform and Jupyter Notebooks to complete the majority of the work.  Packages used include, but are not limited to: pandas, numpy, sklearn, matplotlib, seaborn, and scipy.

Dimensionality Reduction (t-sne) in the Guassian Mixture Modeling (GMM) notebook was completed using an AWS EC2 p2.xlarge instance to reduce processing time, though this is not strictly required.  This phase could likely be improved by rewriting the code in PySpark.

Natural Language Processing (NLP) leveraged the Google Cloud Platform (GCP) to complete sentiment analysis of the individual posts.  Specifically, Google's AutoML model was trained with 1000 labeled posts provided by Sony Music.  New social media posts' sentiment analysis was then predicted on GCP.  This requires the user to sign up for a [GCP account](https://cloud.google.com/automl/).

Social Media Data for Facebook, Instagram, and Twitter were collected through the CrowdTangle platform, provided by Sony Music.  CrowdTangle is owned by Facebook and provides social media statistics to subscribers through an API.  An account is required to access this data.  The API description can be accessed [here](https://github.com/CrowdTangle/API/wiki).

Youtube data was accessed via the public API.  You can request a public API key [here](https://developers.google.com/youtube/v3/).

MusicBrainz data was also accessed via the public API.  Details are provided [here](https://musicbrainz.org/doc/Development/XML_Web_Service/Version_2) and in the MusicBrainz Jupyter notebook.

Artist details (e.g. age, genre) were collected manually through Wikipedia.

## Getting Started

To get started via the [Github page](https://github.com/ghazalerfani/SocialMedia-Music), you will require access to the CrowdTangle data for Facebook, Instagram, and Twitter.  Youtube and MusicBrainz data can be pulled via the public APIs.  The Notebooks used to run the analysis can be found in ./FinalDelivNotebooks.

To get started via the compact zip file (email for access), you need to unzip the folder to your local drive.  The folder will contain the following:

* csv files that include the social media data for Facebook, Instagram, Twitter, Youtube.  The Youtube data was generated using the Youtube_notebook.ipynb.  MusicBrainz.ipynb will generate the album release date data.  The master_artists_list.csv will include artist information and foreign keys to map all the social media data together.  The ArtistList_July2_withDetails.xlsx file is used for Music Brainz mapping.

* Seven Jupyter Notebook files.  The Youtube_notebook.ipynb will access the Youtube API and extract youtube video post information for the supplied artists.  The MusicBrainz.ipynb will do the same for MusicBrainz data.  The Combined Social Data.ipynb will import Facebook, Instagram, Twitter, Youtube, MusicBrainz and Artist lists files and complete all necessary steps to clean and merge the datasets.  It will output a Pickle file that can then be used for subsequent analysis.  The GMM_Model_Final.ipynb, FinalDeliverable_EDA.ipynb, Regression_Final.ipynb and Sentiment Analysis.ipynb Notebooks all load in the Pickle file for their own analytical pipelines.

## Methodologies Used

The following methodologies and tools are used in this project:

* Public API access and data extraction
* Data cleaning, feature creation, dataframe merging
* Standard Scaling, Skew Transformations (PowerTransformer), Cross Validation (GridSearchCV)
* Dimensionality Reduction: Principle Component Analysis (PCA), T-distributed stochastic neighbor embedding (t-sne)
* Regression: Linear Regression, Lasso/Ridge Regression, Random Forest Regression, xgboost
* Clustering: Gaussian Mixture Modeling (GMM)
* Natural Language Processing (NLP)
* Qualitative and Exploratory Data Analysis

## Authors
Zhexin Chen, Ghazal Erfani, Gaurij Hardikar, Daniel Lesser, Phani Krishna Pasumarthi 

## Acknowledgements
Advisor: Michael D. Smith, Professor of Information Technology and Marketing at Carnegie Mellon University, Heinz College
Project Sponsor: Mark Fridson, Director of Data Science at Sony Music Entertainment

Special Thanks:

Shuxuan (Helen) Zeng, PhD Information Systems Candidate at Carnegie Mellon University, Heinz College
Marius Blanchard, Sony Music

