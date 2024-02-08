Place your selected data file into this directory.


1.show exactly two documents from the listings collection in any order
db.listings.find().limit(2);

2.show exactly 10 documents in any order, but "prettyprint" in easier to read format, using the pretty() function.
db.listings.find().limit(10).pretty();

3.choose two hosts (by reffering to their host_id values) who are superhosts (available in the host_is_superhost field), and show all of the listings offered by both of the two hosts
only show the name, price, neighbourhood, host_name, and host_is_superhost for each result

who are superhosts: 1292070 and 1362726

db.listings.find(
    {$or: [
        {host_id:1292070},
        {host_id:1362726}
        ]},
        {_id: 0, name: 1, price: 1,neighbourhood: 1,host_name: 1,host_is_superhost:1});


4.find all the unique host_name values (see the docs)

db.listings.distinct("host_name");


5.find all of the places that have more than 2 beds in a neighborhood of your choice (referred to as either the neighborhood or neighbourhood_group_cleansed fields in the data file), ordered by review_scores_rating descending
only show the name, beds, review_scores_rating, and price
if your data set only has blanks for all the neighborhood-related fields, or only one neighborhood value in all documents, you may pick another field to filter by - include an explanation and justification for this in your report.
if you run out of memory for this query, try filtering review_scores_rating that aren't empty ($ne); and lastly, if there's still an issue, you can set the beds to match exactly 2.

#choose Asheville, North Carolina, United States


db.listings.find({beds:{$gt:2},"neighbourhood_cleansed":28801},{_id: 0,  "name": 1,  "beds": 1,  "review_scores_rating": 1,  "price": 1}).sort({ "review_scores_rating": -1 }).pretty();




6. show the number of listings per host


#I used host id instead of host names here because I think host id is more unqiue
!!!!
db.listings.aggregate([
    { $group: { _id: "$host_id", count: { $sum: 1 } } },
  ])


7.find the average review_scores_rating per neighborhood, and only show the ones above a 95, sorted in descending order of rating (see the docs)
if your data set only has blanks in the neighborhood-related fields, or only one neighborhood value in all documents, you may pick another field to break down the listings by - include an explanation and justification for this in your report.



db.listings.aggregate([
    { $match : { "review_scores_rating" : {$gt:4 } }},
    { $group : { _id:"$neighbourhood" ,  "avgRating":{$avg:"$review_scores_rating"}}},
    { $sort : { "review_scores_rating" : -1 } }
])



db.listings.aggregate( 
    {"$group": { _id: "$host_neighbourhood",averagetet: { $avg: "$review_scores_rating"}}},
    {"$match":{averagetet:{$gt:4.75}}},
    {"$sort":{averagetet:-1}}
    )

