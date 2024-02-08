# AirBnB MongoDB Analysis

## The origin of my data set
My data set is the  AirBnB listings data from Asheville, North Carolina, United States complied on 15 December, 2021. It comes from the Inside Airbnb website's [Data Downloads-Asheville, North Carolina, United States] (http://insideairbnb.com/get-the-data/)

## Format the original data file was
the original data file was in csv.gz file, which is a a CSV file compressed with gzip utility. I used Cyberduck and unzip file command to transfer this compressed file into a csv file, named listings.csv.

## Display raw data from the original data file
It seems that the table could not be displayed properly when the number of columns exceeds 9 so I just omit some columns. 

The the first 20 rows of the original data file is shown as the following:

| id | listing_url | scrape_id |last_scraped|name |host_id |host_url |host_name|host_since|
| ------------- | ------------- |------------- | ------------- |------------- | ------------- |------------- | ------------- |------------- | 
108061|	https://www.airbnb.com/rooms/108061	|20211215062309|	2021-12-15|	Walk to stores/parks/downtown. Fenced yard/Pets OK|320564	|https://www.airbnb.com/users/show/320564	|Lisa	|2010-12-16
155305|	https://www.airbnb.com/rooms/155305	|20211215062309	|2021-12-15	|Cottage! BonPaul + Sharky's Hostel|746673|	https://www.airbnb.com/users/show/746673|	BonPaul	|2011-06-26
156805|	https://www.airbnb.com/rooms/156805|	20211215062309|	2021-12-15|	Private Room "Ader" at BPS Hostel|746673|	https://www.airbnb.com/users/show/746673|	BonPaul	|2011-06-26
156926|	https://www.airbnb.com/rooms/156926	|20211215062309	|2021-12-15	|Mixed Dorm "Top Bunk #1" at BPS Hostel|746673|	https://www.airbnb.com/users/show/746673|	BonPaul	|2011-06-26|
160594|	https://www.airbnb.com/rooms/160594	|20211215062309	|2021-12-15	|Historic Grove Park|769252|	https://www.airbnb.com/users/show/769252|	Elizabeth|	2011-07-02
197263|	https://www.airbnb.com/rooms/197263|	20211215062309|	2021-12-15|	Tranquil Room & Private Bath|961396	|https://www.airbnb.com/users/show/961396|	Timo|	2011-08-12
209068|	https://www.airbnb.com/rooms/209068	|20211215062309	|2021-12-15	|Terrace Cottage|1029919|	https://www.airbnb.com/users/show/1029919|	Kevin	|2011-08-28
246315|	https://www.airbnb.com/rooms/246315 |	20211215062309|	2021-12-15|	Asheville Dreamer's Cabin|1292070|	https://www.airbnb.com/users/show/1292070 |	Annie|	2011-10-14
259576|	https://www.airbnb.com/rooms/259576|	20211215062309|	2021-12-15|	Private, peaceful, and free goat therapy|1362726|	https://www.airbnb.com/users/show/1362726	|Julia	|2011-11-02
295496|	https://www.airbnb.com/rooms/295496|	20211215062309|	2021-12-15|	The Fern Street Apt near Biltmore|1501882	|https://www.airbnb.com/users/show/1501882|	Debbie|	2011-12-13
304379|	https://www.airbnb.com/rooms/304379	|20211215062309|	2021-12-15|	Refocus Cottage - paradise|1566145|	https://www.airbnb.com/users/show/1566145|	Gayle|	2012-01-04
353092|	https://www.airbnb.com/rooms/353092|	20211215062309|	2021-12-15|	Athena's Loft:  Find yourself here!|1788071	|https://www.airbnb.com/users/show/1788071|	Beth|	2012-02-21
427497|	https://www.airbnb.com/rooms/427497|	20211215062309|	2021-12-15|	Luxurious Mountain Guest Suite Apartment|1909922|	https://www.airbnb.com/users/show/1909922	|Milan|	2012-03-12
433646|	https://www.airbnb.com/rooms/433646	|20211215062309|	2021-12-15|	Historic Arts and Craft Home|1931430	|https://www.airbnb.com/users/show/1931430|	Ana|	2012-03-15
436476|	https://www.airbnb.com/rooms/436476|	20211215062309|	2021-12-15|	8 min Walk to DT AVL! Hip, Chic % Sparkling CLEAN|478398|	https://www.airbnb.com/users/show/478398|	Heidi|	2011-04-02
483384|	https://www.airbnb.com/rooms/483384|	20211215062309|	2021-12-15|	Romantic, Moroccan-Influenced Cottage|467421	|https://www.airbnb.com/users/show/467421	|Camille
495111|	https://www.airbnb.com/rooms/495111|	20211215062309|	2021-12-15|	Walk Downtown private bath peaceful|12874214|	https://www.airbnb.com/users/show/12874214|	David	|2014-03-06
498089|	https://www.airbnb.com/rooms/498089	|20211215062309|	2021-12-15|	Urban Getaway - Perfect Location|2164379|	https://www.airbnb.com/users/show/2164379|	Anne Marie|2012-04-17
528535|	https://www.airbnb.com/rooms/528535	|20211215062309|	2021-12-15|	Dwntwn Studio w/ lots of character|2596933	|https://www.airbnb.com/users/show/2596933|	B	|2012-06-10|
621243|	https://www.airbnb.com/rooms/621243	|0211215062309	|2021-12-15|	The birdhouse.Sweet suite! Downtown Roof top deck!|3079174|	https://www.airbnb.com/users/show/3079174|	Molly|	2012-07-28


## Data scrubbing
I did not do any data scrubbing because I think my dataset is pretty clean and organized. 

## Analysis

Q1:show exactly two documents from the listings collection in any order

-Description:
I used find function to display the documents and use limit function to limit the number of documents shown into only 2

-Code:
```ruby
db.listings.find().limit(2);
```

-First three results:

{ "_id" : ObjectId("624ce94f21f2b8ef60adf489"), "id" : 156805, "listing_url" : "https://www.airbnb.com/rooms/156805", "scrape_id" : NumberLong("20211215062309"), "last_scraped" : "2021-12-15", "name" : "Private Room \"Ader\" at BPS Hostel", "description" : "<b>The space</b><br />Private Rooms at Bon Paul and Sharky's Hostel.  Each Private room has a full size bed that sleeps two adults. <br /><br />Self check-in starts at 3pm.  <br /><br />Guests have access to all hostel amenities: full kitchen and bathrooms, wifi and internet, common area and book exchange, and cool international travelers.  <br /><br />We are located in Historic West Asheville, walking distance to amazing restaurants, cafes and pubs, grocery, and Asheville's River Art's District.  <br /><br />Two private bathrooms are shared throughout the hostel.  <br /><br />We are a traveler's hostel and therefore CANNOT BOOK TO LOCALS.", "neighborhood_overview" : "Easy walk to pubs, cafes, bakery, breweries, laundry, grocery, and music", "picture_url" : "https://a0.muscache.com/pictures/23447d55-fa7e-4a2b-8d0b-a8345f8732fb.jpg", "host_id" : 746673, "host_url" : "https://www.airbnb.com/users/show/746673", "host_name" : "BonPaul", "host_since" : "2011-06-26", "host_location" : "Asheville, North Carolina, United States", "host_about" : "We operate two traveler's hostels located in Historic West Asheville, and in Wilmington, NC. Both locations offer wifi and Internet access, full kitchen and bathroom, book exchange and common areas, and bikes to borrow.  \n", "host_response_time" : "within an hour", "host_response_rate" : "100%", "host_acceptance_rate" : "98%", "host_is_superhost" : "f", "host_thumbnail_url" : "https://a0.muscache.com/im/pictures/user/4dff7e77-612f-447a-aea5-464f22f90f58.jpg?aki_policy=profile_small", "host_picture_url" : "https://a0.muscache.com/im/pictures/user/4dff7e77-612f-447a-aea5-464f22f90f58.jpg?aki_policy=profile_x_medium", "host_neighbourhood" : "", "host_listings_count" : 7, "host_total_listings_count" : 7, "host_verifications" : "['email', 'phone', 'facebook', 'reviews', 'offline_government_id', 'selfie', 'government_id', 'identity_manual']", "host_has_profile_pic" : "t", "host_identity_verified" : "t", "neighbourhood" : "Asheville, North Carolina, United States", "neighbourhood_cleansed" : 28806, "neighbourhood_group_cleansed" : "", "latitude" : 35.57864, "longitude" : -82.59578, "property_type" : "Private room in residential home", "room_type" : "Private room", "accommodates" : 2, "bathrooms" : "", "bathrooms_text" : "2.5 shared baths", "bedrooms" : 1, "beds" : 1, "amenities" : "[\"Long term stays allowed\", \"Essentials\", \"Microwave\", \"Refrigerator\", \"Keypad\", \"Kitchen\", \"Smoke alarm\", \"Backyard\", \"Wifi\", \"Hot water\", \"Free parking on premises\", \"Cooking basics\", \"Breakfast\", \"Coffee maker\", \"Fire extinguisher\", \"Carbon monoxide alarm\", \"Heating\", \"Dishes and silverware\", \"Free street parking\", \"Lock on bedroom door\"]", "price" : "$66.00", "minimum_nights" : 1, "maximum_nights" : 365, "minimum_minimum_nights" : 1, "maximum_minimum_nights" : 1, "minimum_maximum_nights" : 365, "maximum_maximum_nights" : 365, "minimum_nights_avg_ntm" : 1, "maximum_nights_avg_ntm" : 365, "calendar_updated" : "", "has_availability" : "t", "availability_30" : 0, "availability_60" : 0, "availability_90" : 0, "availability_365" : 0, "calendar_last_scraped" : "2021-12-15", "number_of_reviews" : 67, "number_of_reviews_ltm" : 0, "number_of_reviews_l30d" : 0, "first_review" : "2011-09-20", "last_review" : "2020-01-01", "review_scores_rating" : 4.52, "review_scores_accuracy" : 4.73, "review_scores_cleanliness" : 4.43, "review_scores_checkin" : 4.76, "review_scores_communication" : 4.61, "review_scores_location" : 4.84, "review_scores_value" : 4.46, "license" : "", "instant_bookable" : "t", "calculated_host_listings_count" : 7, "calculated_host_listings_count_entire_homes" : 1, "calculated_host_listings_count_private_rooms" : 2, "calculated_host_listings_count_shared_rooms" : 4, "reviews_per_month" : 0.54 }
{ "_id" : ObjectId("624ce94f21f2b8ef60adf488"), "id" : 108061, "listing_url" : "https://www.airbnb.com/rooms/108061", "scrape_id" : NumberLong("20211215062309"), "last_scraped" : "2021-12-15", "name" : "Walk to stores/parks/downtown. Fenced yard/Pets OK", "description" : "Walk to town in ten minutes! Monthly rental includes utilities, wifi, linens and everything you'll need to make a home in downtown Asheville. Quiet and friendly neighborhood, one mile from the hospital or UNCA. Fenced private backyard and private deck. Private laundry room and lock up spot for your bike. Dedicated parking spot. Please contact me in advance if you want to bring your pet(s). I will not allow pets without prior disclosure. There is a security deposit required for all pets.<br /><br /><b>The space</b><br />True Asheville...artist styled apartment with a pet friendly fenced back yard and great neighbors all around. Stay here and easily walk downtown or through the wooded trails and botanical gardens at UNCA. Super convenient neighborhood to walk, bike, run or just stroll around and meet people....very local and friendly! Whole Foods, Trader Joe’s and lots of nearby coffee shops, restaurants and Asheville Yoga Center all within a four block radius. <br /><br />Your sunny dow", "neighborhood_overview" : "I love my neighborhood! Its friendly, easy-going, quiet and the closest one to downtown, groceries, yoga and coffee shops. There's woods with trails nearby to walk your dog and commune with the trees. You really don't need a car here, everything is minutes away on foot or by bike.", "picture_url" : "https://a0.muscache.com/pictures/41011975/0cdfc74f_original.jpg", "host_id" : 320564, "host_url" : "https://www.airbnb.com/users/show/320564", "host_name" : "Lisa", "host_since" : "2010-12-16", "host_location" : "Mills River, North Carolina, United States", "host_about" : "I am a long time resident of Asheville and am glad help you find great hikes, yoga, dog parks, kids activities, etc.", "host_response_time" : "within an hour", "host_response_rate" : "100%", "host_acceptance_rate" : "33%", "host_is_superhost" : "f", "host_thumbnail_url" : "https://a0.muscache.com/im/users/320564/profile_pic/1394193052/original.jpg?aki_policy=profile_small", "host_picture_url" : "https://a0.muscache.com/im/users/320564/profile_pic/1394193052/original.jpg?aki_policy=profile_x_medium", "host_neighbourhood" : "", "host_listings_count" : 2, "host_total_listings_count" : 2, "host_verifications" : "['email', 'phone', 'facebook', 'reviews', 'offline_government_id', 'kba', 'government_id']", "host_has_profile_pic" : "t", "host_identity_verified" : "t", "neighbourhood" : "Asheville, North Carolina, United States", "neighbourhood_cleansed" : 28801, "neighbourhood_group_cleansed" : "", "latitude" : 35.6067, "longitude" : -82.55563, "property_type" : "Entire rental unit", "room_type" : "Entire home/apt", "accommodates" : 2, "bathrooms" : "", "bathrooms_text" : "1 bath", "bedrooms" : 1, "beds" : 1, "amenities" : "[\"Essentials\", \"Dedicated workspace\", \"Refrigerator\", \"Kitchen\", \"Indoor fireplace\", \"Dishwasher\", \"Private entrance\", \"Hangers\", \"Coffee maker\", \"Iron\", \"Dining table\", \"Wine glasses\", \"Long term stays allowed\", \"Oven\", \"Clothing storage\", \"Ceiling fan\", \"Cooking basics\", \"Carbon monoxide alarm\", \"Microwave\", \"Heating\", \"Bed linens\", \"Patio or balcony\", \"Cleaning products\", \"Smoke alarm\", \"Dryer\", \"Hot water\", \"Free parking on premises\", \"Outdoor dining area\", \"Host greets you\", \"Wifi\", \"Washer\", \"Free street parking\", \"BBQ grill\", \"Freezer\", \"Backyard\", \"Extra pillows and blankets\", \"Stove\", \"Air conditioning\", \"Toaster\", \"Dishes and silverware\"]", "price" : "$120.00", "minimum_nights" : 30, "maximum_nights" : 365, "minimum_minimum_nights" : 30, "maximum_minimum_nights" : 30, "minimum_maximum_nights" : 1125, "maximum_maximum_nights" : 1125, "minimum_nights_avg_ntm" : 30, "maximum_nights_avg_ntm" : 1125, "calendar_updated" : "", "has_availability" : "t", "availability_30" : 22, "availability_60" : 49, "availability_90" : 76, "availability_365" : 344, "calendar_last_scraped" : "2021-12-15", "number_of_reviews" : 89, "number_of_reviews_ltm" : 0, "number_of_reviews_l30d" : 0, "first_review" : "2011-09-21", "last_review" : "2019-11-30", "review_scores_rating" : 4.49, "review_scores_accuracy" : 4.57, "review_scores_cleanliness" : 4.7, "review_scores_checkin" : 4.85, "review_scores_communication" : 4.79, "review_scores_location" : 4.84, "review_scores_value" : 4.48, "license" : "", "instant_bookable" : "f", "calculated_host_listings_count" : 2, "calculated_host_listings_count_entire_homes" : 2, "calculated_host_listings_count_private_rooms" : 0, "calculated_host_listings_count_shared_rooms" : 0, "reviews_per_month" : 0.71 }
> 


-Insights: If a consumer just want to find 2 AirBnB without any requirement, we could show consumers all infomation we have about thses 2 houses using this command since it shows 2 whole document. 



Q2:show exactly 10 documents in any order, but "prettyprint" in easier to read format, using the pretty() function.

-Description: I still used the find function to show result, which is pretty similar to the first one, but we limit the documents number into 10 using .limit(10) after find function. Then, "prettyprint" in easier to read format using .pretty().


-Code:
```ruby
db.listings.find().limit(10).pretty();
```

-First three results:

{
	"_id" : ObjectId("624ce94f21f2b8ef60adf489"),
	"id" : 156805,
	"listing_url" : "https://www.airbnb.com/rooms/156805",
	"scrape_id" : NumberLong("20211215062309"),
	"last_scraped" : "2021-12-15",
	"name" : "Private Room \"Ader\" at BPS Hostel",
	"description" : "<b>The space</b><br />Private Rooms at Bon Paul and Sharky's Hostel.  Each Private room has a full size bed that sleeps two adults. <br /><br />Self check-in starts at 3pm.  <br /><br />Guests have access to all hostel amenities: full kitchen and bathrooms, wifi and internet, common area and book exchange, and cool international travelers.  <br /><br />We are located in Historic West Asheville, walking distance to amazing restaurants, cafes and pubs, grocery, and Asheville's River Art's District.  <br /><br />Two private bathrooms are shared throughout the hostel.  <br /><br />We are a traveler's hostel and therefore CANNOT BOOK TO LOCALS.",
	"neighborhood_overview" : "Easy walk to pubs, cafes, bakery, breweries, laundry, grocery, and music",
	"picture_url" : "https://a0.muscache.com/pictures/23447d55-fa7e-4a2b-8d0b-a8345f8732fb.jpg",
	"host_id" : 746673,
	"host_url" : "https://www.airbnb.com/users/show/746673",
	"host_name" : "BonPaul",
	"host_since" : "2011-06-26",
	"host_location" : "Asheville, North Carolina, United States",
	"host_about" : "We operate two traveler's hostels located in Historic West Asheville, and in Wilmington, NC. Both locations offer wifi and Internet access, full kitchen and bathroom, book exchange and common areas, and bikes to borrow.  \n",
	"host_response_time" : "within an hour",
	"host_response_rate" : "100%",
	"host_acceptance_rate" : "98%",
	"host_is_superhost" : "f",
	"host_thumbnail_url" : "https://a0.muscache.com/im/pictures/user/4dff7e77-612f-447a-aea5-464f22f90f58.jpg?aki_policy=profile_small",
	"host_picture_url" : "https://a0.muscache.com/im/pictures/user/4dff7e77-612f-447a-aea5-464f22f90f58.jpg?aki_policy=profile_x_medium",
	"host_neighbourhood" : "",
	"host_listings_count" : 7,
	"host_total_listings_count" : 7,
	"host_verifications" : "['email', 'phone', 'facebook', 'reviews', 'offline_government_id', 'selfie', 'government_id', 'identity_manual']",
	"host_has_profile_pic" : "t",
	"host_identity_verified" : "t",
	"neighbourhood" : "Asheville, North Carolina, United States",
	"neighbourhood_cleansed" : 28806,
	"neighbourhood_group_cleansed" : "",
	"latitude" : 35.57864,
	"longitude" : -82.59578,
	"property_type" : "Private room in residential home",
	"room_type" : "Private room",
	"accommodates" : 2,
	"bathrooms" : "",
	"bathrooms_text" : "2.5 shared baths",
	"bedrooms" : 1,
	"beds" : 1,
	"amenities" : "[\"Long term stays allowed\", \"Essentials\", \"Microwave\", \"Refrigerator\", \"Keypad\", \"Kitchen\", \"Smoke alarm\", \"Backyard\", \"Wifi\", \"Hot water\", \"Free parking on premises\", \"Cooking basics\", \"Breakfast\", \"Coffee maker\", \"Fire extinguisher\", \"Carbon monoxide alarm\", \"Heating\", \"Dishes and silverware\", \"Free street parking\", \"Lock on bedroom door\"]",
	"price" : "$66.00",
	"minimum_nights" : 1,
	"maximum_nights" : 365,
	"minimum_minimum_nights" : 1,
	"maximum_minimum_nights" : 1,
	"minimum_maximum_nights" : 365,
	"maximum_maximum_nights" : 365,
	"minimum_nights_avg_ntm" : 1,
	"maximum_nights_avg_ntm" : 365,
	"calendar_updated" : "",
	"has_availability" : "t",
	"availability_30" : 0,
	"availability_60" : 0,
	"availability_90" : 0,
	"availability_365" : 0,
	"calendar_last_scraped" : "2021-12-15",
	"number_of_reviews" : 67,
	"number_of_reviews_ltm" : 0,
	"number_of_reviews_l30d" : 0,
	"first_review" : "2011-09-20",
	"last_review" : "2020-01-01",
	"review_scores_rating" : 4.52,
	"review_scores_accuracy" : 4.73,
	"review_scores_cleanliness" : 4.43,
	"review_scores_checkin" : 4.76,
	"review_scores_communication" : 4.61,
	"review_scores_location" : 4.84,
	"review_scores_value" : 4.46,
	"license" : "",
	"instant_bookable" : "t",
	"calculated_host_listings_count" : 7,
	"calculated_host_listings_count_entire_homes" : 1,
	"calculated_host_listings_count_private_rooms" : 2,
	"calculated_host_listings_count_shared_rooms" : 4,
	"reviews_per_month" : 0.54
}
{
	"_id" : ObjectId("624ce94f21f2b8ef60adf488"),
	"id" : 108061,
	"listing_url" : "https://www.airbnb.com/rooms/108061",
	"scrape_id" : NumberLong("20211215062309"),
	"last_scraped" : "2021-12-15",
	"name" : "Walk to stores/parks/downtown. Fenced yard/Pets OK",
	"description" : "Walk to town in ten minutes! Monthly rental includes utilities, wifi, linens and everything you'll need to make a home in downtown Asheville. Quiet and friendly neighborhood, one mile from the hospital or UNCA. Fenced private backyard and private deck. Private laundry room and lock up spot for your bike. Dedicated parking spot. Please contact me in advance if you want to bring your pet(s). I will not allow pets without prior disclosure. There is a security deposit required for all pets.<br /><br /><b>The space</b><br />True Asheville...artist styled apartment with a pet friendly fenced back yard and great neighbors all around. Stay here and easily walk downtown or through the wooded trails and botanical gardens at UNCA. Super convenient neighborhood to walk, bike, run or just stroll around and meet people....very local and friendly! Whole Foods, Trader Joe’s and lots of nearby coffee shops, restaurants and Asheville Yoga Center all within a four block radius. <br /><br />Your sunny dow",
	"neighborhood_overview" : "I love my neighborhood! Its friendly, easy-going, quiet and the closest one to downtown, groceries, yoga and coffee shops. There's woods with trails nearby to walk your dog and commune with the trees. You really don't need a car here, everything is minutes away on foot or by bike.",
	"picture_url" : "https://a0.muscache.com/pictures/41011975/0cdfc74f_original.jpg",
	"host_id" : 320564,
	"host_url" : "https://www.airbnb.com/users/show/320564",
	"host_name" : "Lisa",
	"host_since" : "2010-12-16",
	"host_location" : "Mills River, North Carolina, United States",
	"host_about" : "I am a long time resident of Asheville and am glad help you find great hikes, yoga, dog parks, kids activities, etc.",
	"host_response_time" : "within an hour",
	"host_response_rate" : "100%",
	"host_acceptance_rate" : "33%",
	"host_is_superhost" : "f",
	"host_thumbnail_url" : "https://a0.muscache.com/im/users/320564/profile_pic/1394193052/original.jpg?aki_policy=profile_small",
	"host_picture_url" : "https://a0.muscache.com/im/users/320564/profile_pic/1394193052/original.jpg?aki_policy=profile_x_medium",
	"host_neighbourhood" : "",
	"host_listings_count" : 2,
	"host_total_listings_count" : 2,
	"host_verifications" : "['email', 'phone', 'facebook', 'reviews', 'offline_government_id', 'kba', 'government_id']",
	"host_has_profile_pic" : "t",
	"host_identity_verified" : "t",
	"neighbourhood" : "Asheville, North Carolina, United States",
	"neighbourhood_cleansed" : 28801,
	"neighbourhood_group_cleansed" : "",
	"latitude" : 35.6067,
	"longitude" : -82.55563,
	"property_type" : "Entire rental unit",
	"room_type" : "Entire home/apt",
	"accommodates" : 2,
	"bathrooms" : "",
	"bathrooms_text" : "1 bath",
	"bedrooms" : 1,
	"beds" : 1,
	"amenities" : "[\"Essentials\", \"Dedicated workspace\", \"Refrigerator\", \"Kitchen\", \"Indoor fireplace\", \"Dishwasher\", \"Private entrance\", \"Hangers\", \"Coffee maker\", \"Iron\", \"Dining table\", \"Wine glasses\", \"Long term stays allowed\", \"Oven\", \"Clothing storage\", \"Ceiling fan\", \"Cooking basics\", \"Carbon monoxide alarm\", \"Microwave\", \"Heating\", \"Bed linens\", \"Patio or balcony\", \"Cleaning products\", \"Smoke alarm\", \"Dryer\", \"Hot water\", \"Free parking on premises\", \"Outdoor dining area\", \"Host greets you\", \"Wifi\", \"Washer\", \"Free street parking\", \"BBQ grill\", \"Freezer\", \"Backyard\", \"Extra pillows and blankets\", \"Stove\", \"Air conditioning\", \"Toaster\", \"Dishes and silverware\"]",
	"price" : "$120.00",
	"minimum_nights" : 30,
	"maximum_nights" : 365,
	"minimum_minimum_nights" : 30,
	"maximum_minimum_nights" : 30,
	"minimum_maximum_nights" : 1125,
	"maximum_maximum_nights" : 1125,
	"minimum_nights_avg_ntm" : 30,
	"maximum_nights_avg_ntm" : 1125,
	"calendar_updated" : "",
	"has_availability" : "t",
	"availability_30" : 22,
	"availability_60" : 49,
	"availability_90" : 76,
	"availability_365" : 344,
	"calendar_last_scraped" : "2021-12-15",
	"number_of_reviews" : 89,
	"number_of_reviews_ltm" : 0,
	"number_of_reviews_l30d" : 0,
	"first_review" : "2011-09-21",
	"last_review" : "2019-11-30",
	"review_scores_rating" : 4.49,
	"review_scores_accuracy" : 4.57,
	"review_scores_cleanliness" : 4.7,
	"review_scores_checkin" : 4.85,
	"review_scores_communication" : 4.79,
	"review_scores_location" : 4.84,
	"review_scores_value" : 4.48,
	"license" : "",
	"instant_bookable" : "f",
	"calculated_host_listings_count" : 2,
	"calculated_host_listings_count_entire_homes" : 2,
	"calculated_host_listings_count_private_rooms" : 0,
	"calculated_host_listings_count_shared_rooms" : 0,
	"reviews_per_month" : 0.71
}
{
	"_id" : ObjectId("624ce94f21f2b8ef60adf48a"),
	"id" : 155305,
	"listing_url" : "https://www.airbnb.com/rooms/155305",
	"scrape_id" : NumberLong("20211215062309"),
	"last_scraped" : "2021-12-15",
	"name" : "Cottage! BonPaul + Sharky's Hostel",
	"description" : "<b>The space</b><br />Private cottage located behind the main house at the Hostel in Historic West Asheville.  <br /><br />Self check-in starts at 3pm.<br /><br />Cottage has full size bed, private kitchen and bathroom. Please note also, the shower is not huge. It will fit one person just fine. <br /><br />Guests get full access to the hostel: book exchange, community computer, common areas with cool international travelers and all the cool restaurants, pubs and cafe's that West Asheville has within walking distance!<br /><br /><b>Guest access</b><br />Guests have solo access to the cottage, and access to the main house of the hostel.<br /><br /><b>Other things to note</b><br />Parking in our lot is limited. You can also park for free on the street.",
	"neighborhood_overview" : "We are within easy walk of pubs, breweries, music, thrift shops, grocery, bakery, cafes, and restaurants in the hip West Asheville neighborhood. We are about 2.7 miles from the center of town.",
	"picture_url" : "https://a0.muscache.com/pictures/8880711/cf38d21c_original.jpg",
	"host_id" : 746673,
	"host_url" : "https://www.airbnb.com/users/show/746673",
	"host_name" : "BonPaul",
	"host_since" : "2011-06-26",
	"host_location" : "Asheville, North Carolina, United States",
	"host_about" : "We operate two traveler's hostels located in Historic West Asheville, and in Wilmington, NC. Both locations offer wifi and Internet access, full kitchen and bathroom, book exchange and common areas, and bikes to borrow.  \n",
	"host_response_time" : "within an hour",
	"host_response_rate" : "100%",
	"host_acceptance_rate" : "98%",
	"host_is_superhost" : "f",
	"host_thumbnail_url" : "https://a0.muscache.com/im/pictures/user/4dff7e77-612f-447a-aea5-464f22f90f58.jpg?aki_policy=profile_small",
	"host_picture_url" : "https://a0.muscache.com/im/pictures/user/4dff7e77-612f-447a-aea5-464f22f90f58.jpg?aki_policy=profile_x_medium",
	"host_neighbourhood" : "",
	"host_listings_count" : 7,
	"host_total_listings_count" : 7,
	"host_verifications" : "['email', 'phone', 'facebook', 'reviews', 'offline_government_id', 'selfie', 'government_id', 'identity_manual']",
	"host_has_profile_pic" : "t",
	"host_identity_verified" : "t",
	"neighbourhood" : "Asheville, North Carolina, United States",
	"neighbourhood_cleansed" : 28806,
	"neighbourhood_group_cleansed" : "",
	"latitude" : 35.57864,
	"longitude" : -82.59578,
	"property_type" : "Entire guesthouse",
	"room_type" : "Entire home/apt",
	"accommodates" : 2,
	"bathrooms" : "",
	"bathrooms_text" : "1 bath",
	"bedrooms" : 1,
	"beds" : 1,
	"amenities" : "[\"Essentials\", \"Dedicated workspace\", \"Refrigerator\", \"Kitchen\", \"Hair dryer\", \"Shampoo\", \"Private entrance\", \"Hangers\", \"Coffee maker\", \"Fire extinguisher\", \"Iron\", \"Long term stays allowed\", \"Oven\", \"Cooking basics\", \"Microwave\", \"Heating\", \"Patio or balcony\", \"Smoke alarm\", \"Hot water\", \"Free parking on premises\", \"Wifi\", \"Free street parking\", \"Keypad\", \"Stove\", \"Air conditioning\", \"Dishes and silverware\"]",
	"price" : "$90.00",
	"minimum_nights" : 1,
	"maximum_nights" : 365,
	"minimum_minimum_nights" : 1,
	"maximum_minimum_nights" : 1,
	"minimum_maximum_nights" : 7,
	"maximum_maximum_nights" : 365,
	"minimum_nights_avg_ntm" : 1,
	"maximum_nights_avg_ntm" : 109.9,
	"calendar_updated" : "",
	"has_availability" : "t",
	"availability_30" : 19,
	"availability_60" : 47,
	"availability_90" : 77,
	"availability_365" : 244,
	"calendar_last_scraped" : "2021-12-15",
	"number_of_reviews" : 347,
	"number_of_reviews_ltm" : 68,
	"number_of_reviews_l30d" : 2,
	"first_review" : "2011-07-31",
	"last_review" : "2021-12-05",
	"review_scores_rating" : 4.57,
	"review_scores_accuracy" : 4.69,
	"review_scores_cleanliness" : 4.4,
	"review_scores_checkin" : 4.82,
	"review_scores_communication" : 4.76,
	"review_scores_location" : 4.93,
	"review_scores_value" : 4.53,
	"license" : "",
	"instant_bookable" : "t",
	"calculated_host_listings_count" : 7,
	"calculated_host_listings_count_entire_homes" : 1,
	"calculated_host_listings_count_private_rooms" : 2,
	"calculated_host_listings_count_shared_rooms" : 4,
	"reviews_per_month" : 2.75
}



-Insights: We could give consumers 10 different AirBnB now and pull out all their relevant info and show them to our consumers in an organized and nicer way by using the pretty function. Since it could be in any order, there is no need for us to use any filter. 


Q3:choose two hosts...

-Description: The two hosts I choose who are superhosts are ones with host_id values 1292070 and 1362726. Since we need to show all of the listings offered by both of the two hosts, $or operator here would be necessary. Since we only want to show certain fields (name, price, neighbourhood, host_name, and host_is_superhost), we should write them in the projection. 

-Code:
```ruby
db.listings.find(
    {$or: [
        {host_id:1292070},
        {host_id:1362726}
        ]},
        {_id: 0, name: 1, price: 1,neighbourhood: 1,host_name: 1,host_is_superhost:1});
```

-First three results:

{ "name" : "Asheville Dreamer's Cabin", "host_name" : "Annie", "host_is_superhost" : "t", "neighbourhood" : "", "price" : "$68.00" }
{ "name" : "Private, peaceful, and free goat therapy", "host_name" : "Julia", "host_is_superhost" : "t", "neighbourhood" : "", "price" : "$76.00" }
{ "name" : "Studio apartment in tranquil setting", "host_name" : "Annie", "host_is_superhost" : "t", "neighbourhood" : "", "price" : "$60.00" }
{ "name" : "One bedroom tree house", "host_name" : "Annie", "host_is_superhost" : "t", "neighbourhood" : "", "price" : "$65.00" }

-Insights: For these 2 superhosts, their AirBnB's prices are relatively cheap, which is around $60-$80. Also. the houses they offered usually are quite and within forest, e.g. a abin or tree houses. This query could help consumers who want to live in houses offered by superhosts and compare their prices, neighborhood and other info. 


Q4:find all the unique host_name values 

-Description: dinstinct function could could retrieve distinct values for a given field (host_name field in this case).

-Code:
```ruby
db.listings.distinct("host_name");
```

-First three results (more than 3 are shown here):

    NaN,
	"AJ & Jenn",
	"Aaron",
	"Adam",
	"Adam And Claudia",
	"Adi",
	"Adrienne",
	"Afua",
	"Agnes"

-Insights: If AirBnB company want to have a list of hosts in Asheville, North Carolina, United States, this query could be used. It will pull out all distinct host names in this area. However, it may omit hosts with same names and count them as 1 person so host_id would be a more reliable indicator than host_name. 


Q5:find all of the places that have more than 2 beds...

-Description: Find places that have more than 2 beds in neighborhood 28801 and order by review_scores_rating descending using the sort funtion with the field we are going to sort and -1 represents a descending order. Show the assigned fields by writing them in the projection. Also, I get rid of the null values using  "review_scores_rating":{$ne:""}, so data could be ordered in a descending order based on review_scores_rating. 

-Code:
```ruby
db.listings.find({beds:{$gt:2},"neighbourhood_cleansed":28801,  "review_scores_rating":{$ne:""}},{_id: 0,  "name": 1,  "beds": 1,  "review_scores_rating": 1,  "price": 1}).sort({ "review_scores_rating": -1 }).pretty();
```

-First three results:

{
	"name" : "At Home in Asheville: Comfort, Location, Amenities",
	"beds" : 6,
	"price" : "$150.00",
	"review_scores_rating" : 5
}
{
	"name" : "Historic Asheville Home - Montford (Walk Downtown)",
	"beds" : 5,
	"price" : "$250.00",
	"review_scores_rating" : 5
}
{
	"name" : "Cate's Cottage",
	"beds" : 3,
	"price" : "$200.00",
	"review_scores_rating" : 5
}

-Insights: We could find that places that have more than 2 beds in neighborhood 28801 are relatively expensive, and their prices are among $150-250, which indicates a generally positive relationship between the number of rooms an AirBnB has and the price it is charged (but there are exceptions, e.g the house with 6 beds is cheaper than the house with 5 beds). This query could be useful for consumers travel with family members and they would want to live in a good place, which could be told from the review_scores_rating. 

Q6:show the number of listings per host

-Description: by using $group, we could groupby based on host_id field and do a count, so we could know the number of listings per host. 

I used host id instead of host names here because I think host id is more unqiue

-Code:
```ruby
db.listings.aggregate([
    { $group: { _id: "$host_id", count: { $sum: 1 } } },
  ])
```

-First three results:

{ "_id" : 76587198, "count" : 1 }
{ "_id" : 104157675, "count" : 1 }
{ "_id" : 167540324, "count" : 1 }

-Insights: Most hosts have only 1 listings. Some hosts have more listings like 2 or 5. AirBnB company could use this query to find the hosts offering high number of listings and have a long term copperation with them. Also, since most hosts only have 1 listing, AirBnB company could know who are the major house providers and find ways to encourage them offer more better houses. 


Q7:find the average review_scores_rating per neighborhood

-Description: find average review_scores_rating per neighborhood by using $avg of eview_scores_rating field. Also, we need to limit review_scores_rating to above 4, so using $group is necessay. Besides, $sort and -1 argument could sorted in descending order of rating. The order of these pipeline stages matters. 

-Code:
```ruby
db.listings.aggregate(
    { $group : { _id:"$host_neighbourhood" ,  "avgrating":{$avg:"$review_scores_rating"}}},
    { $match : {"avgrating" : {$gt:4 } }},
    { $sort : { "avgrating" : -1 } }
)
```

-First three results:

{ "_id" : "Midtown", "avgrating" : 5 }
{ "_id" : "Chestnut Hills", "avgrating" : 5 }
{ "_id" : "Mountainbrook", "avgrating" : 5 }

-Insights: Some neighborhoods have very high review_scores_rating, which is full mark 5. And some others also have very high marks. According to their names, we could interpet that neighborhood with high ratings are usually those in the center of the city and with good views (near mountain, river, hills, and brooks). Also, this query is useful for consumers who want to live in a good neighborhood when picking their AirBnB. 




