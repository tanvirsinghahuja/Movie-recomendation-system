# Movie Recommender
## Project Goal
Create a movie recommender based on movie ratings, tags, and genres. This movie recommender includes several filters such as: popularity based filtering, content based filtering, collaborate filtering, and hybrid based filtering.
## Dataset
The dataset for this project can be found here: https://grouplens.org/datasets/movielens/20m/
The ml-20m.zip contains the necessary csv files.
## Approach
Data Preprocessing
* Relevant data was imported
* Data was sliced down to 1m rows to account for limitations in RAM
* Created a pivot table of movie IDs, user IDs, and user ratings
* Timestamp column was dropped, 'no genre listed' and empty tags replaced with ' '
* 'full_metadata' data frame created by joining cleaned userID, movieID, and tag data frames

Content Based Filtering Prep
* TF-IDF vectorizer used on 'full_metadata'
* TruncatedSVD used to truncate and created a latent_matrix_df from vectored 'full_metadata' dataframe

Collaborative Filtering Prep
* latent_matrix_2_df truncated and created with TruncatedSVD on the original pivot table created during the data preprocessing steps above
* Consine similarity matrix created to be used to find similarity between the movies
## Results
### Popularity Based Filtering
* Weighted rating calculated to consider a minimum number of votes and the mean vote for all users who watched a certain movie
* Filtered to Top 10

![popularity_recommender](https://user-images.githubusercontent.com/83191235/154214037-b4b37236-686d-4b80-8743-97bf0e749c07.PNG)

### Collaborative, Content and Hybrid Recommender - In One!
Function created to allow for Top 15 movies to be shown based on either Content Based Filtering, Collaborative Based Filtering, or Hybrid Based Filtering (combining content and collaborative scores at a weight of 50/50 for this code). Movie title and scoring type are the passed parameters for the function.

![movie_recommender_function](https://user-images.githubusercontent.com/83191235/154210681-4bb5a2eb-9a0e-42df-8cde-093fdf04b8fc.PNG)

### Matrix Factorization Recommender
This is another way to accomplish collaborative filtering by finding the relationship between items and users entities.

![matrix_factor_recommender](https://user-images.githubusercontent.com/83191235/154213785-5814ef0d-8f22-4419-9471-fd2fb8ee66af.PNG)

### Surprise - Another Way
The surprise library was used to call the Single Value Decomposition algorithm to train and create an algorithm that would give movie recommendations based on the individual user.

![surprise_movie_recommender](https://user-images.githubusercontent.com/83191235/154211157-2c5f8061-aaf6-4cdf-b20e-c3284a1b801a.PNG)

## Recommendations Scores
Hybrid recommendation score for Toy Story (1995) passed in as the movie 
![hybrid_scoring_recommender](https://user-images.githubusercontent.com/83191235/154212029-62caf660-ae5c-4e19-91d3-5dbf4e3a02be.PNG)

Surprise user movie recommendations based on algorithms predictions for User 11141
![surprise_user_recommender](https://user-images.githubusercontent.com/83191235/154212136-84accbcd-e9c9-4680-9627-093325df5720.PNG)
