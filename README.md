# SQL_A_Simple_Movie_Recommendation_Database
# Description of each table:
A. users:userid(int,primarykey),name(text)
B. movies:movieid(integer,primarykey),title(text)
C. taginfo:tagid(int,primarykey),content(text)
D. genres:genreid(integer,primarykey),name(text)
E. ratings:userid(int,foreignkey),movieid(int,foreignkey),rating(numeric),
timestamp (bigint, seconds since midnight Coordinated Universal Time (UTC) of January 1, 1970)
F. tags: userid (int, foreign key), movieid (int, foreign key), tagid (int, foreign key), timestamp (bigint, seconds since midnight Coordinated Universal Time (UTC) of January 1, 1970).
G. hasagenre: movieid (int, foreign key), genreid (int, foreign key)
# The algorithm for movie recommendation.
Given a userID v1, you need to recommend the movies according to the movies he has rated before. In particular, we predict the rating P of a movie “i” that the user “Ua” didn’t rate. In the following recommendation model, P(Ua, i) is the predicted rating of movie i for User Ua. L contains all movies that have been rated by Ua. Sim(i,l) is the similarity between i and l. r is the rating that Ua gave to l.
 
we want to return predicted ratings from all movies that the given user hasn’t rated yet. and we only return the movies whose predicted ratings are >3.9. 

In order to produce the recommendation table, we first need to calculate the similarities between every pair of two movies. The similarity is equal to the similarity of the average ratings of two movies (average rating over all users, the average ratings in Query 5). That means, if the average ratings of two movies are more close, the two movies are more similar. The similarity score is a fractional value E [0, 1]. 0 means not similar at all, 1 means very similar. To summarize, the similarity between two movies, i and l, is calculated using the equation below. Abs() is to take the absolute value.
