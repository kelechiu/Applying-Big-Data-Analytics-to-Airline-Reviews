# Applying-Big-Data-Analytics-to-Airline-Reviews
# 1. Introduction

The airline industry operates in a highly competitive and dynamic market, with airlines constantly adapting to changing market demands and advancements in technology in order to achieve customer satisfaction and loyalty. One critical success factor for airlines is their ability to understand what influences customer behaviour and how their preferences impact the overall business.

By utilizing various statistical methods, this research aims to examine online reviews and identify the attributes that have an impact on passengers’ overall satisfaction and contribute to a successful travel experience.

# 2. Research Questions and Hypotheses
### What factors significantly influence customers' choices during holiday bookings?
H0: No significant difference in Rating among Class and Traveller_Type.
H1: There is a significant difference in Rating among Class and Traveller_type.

### How does the timing of holiday bookings influence customer behaviour and choices?
H0: No significant difference in Rating among Travel_Month.
H1: There is a significant difference in Rating among Travel_Month.

### Can customer characteristics predict the likelihood of a successful holiday booking?
H0: Traveller characteristics cannot predict the likelihood of a successful holiday booking. 
H1: Traveller characteristics can predict the likelihood of a successful holiday booking.


# 3. Data Description

The dataset is a collection of airline reviews, displaying the experiences and feedback of airline passengers. It is the primary data source for this project, and it will be used to investigate passenger sentiments, choices, and potential areas of improvement within the airline industry. The dataset has 3580 rows each representing a unique passenger’s flight details and experience. It also has 9 columns/variables that are described in detail below:

<img width="447" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/a224b087-dda5-405f-bcfe-14818109e68c">



# 4	Data Cleaning Methods

Data cleaning is the most important step in any data analysis process because it ensures the dataset is accurate and complete for further exploration and analysis. Some common steps in data cleaning and pre-processing include handling missing values, outliers and duplicates, encoding categorical variables, handling inconsistencies and handling text data (tokenization, removing stop words, stemming and lemmatization).

# 4.1.	Dataset Inspection

To begin the analysis process, I imported all necessary libraries in Jupyter Notebook and read the dataset as a Pandas DataFrame. Pandas is a powerful tool for data manipulation, cleaning and transformation. Similarly, dataFrame operations structure the dataset into rows and columns, allowing for easier grouping, merging and reshaping tasks.

<img width="344" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/c47b5d7f-fbe6-4e06-a6fb-57c1e8ece262">

<img width="451" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/9644055e-3c1c-415c-ab81-657c954aa2d8">

I viewed a sample of the dataset and at first glance, it appears to have some inconsistencies and missing values. Values have been inputted in the wrong columns, for instance, Flying_month column contains values belonging to Route column and Class column contains values belonging to Traveller_type. Traveller_type has values that represent aircraft information and the Review_content column contains route and flying_month information that will be extracted. Class column also contains values (‘yes’, ‘no’) that should be moved to a new column representing if passengers would recommend the airline or not.

<img width="279" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/6f6c985e-b11d-4155-91da-da5f918c58cd">

As seen above, the dataset has 3580 rows and 9 columns. There are also missing values in the dataset and the data types for rating and flying_month are wrong.

## 4.2. Handling Data Misplacement

Data misplacement occurs when values intended for one column are wrongly entered into another column. This can occur as a result of data entry errors or data extraction issues. Handling misplaced data prevents inaccurate conclusions and ensures the dataset is consistently accurate. To do this, I checked for unique values in each column and moved the incorrect entries to their respective columns or new columns.

### Create ‘Aircraft’ Column

As seen in the figure below, traveller_type column contains aircraft entries, so I created a new column called ‘Aircraft’ and moved them there. 

<img width="303" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/21893aba-b072-4c50-bfb1-5a937a8adfb5">

<img width="327" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/3db99a03-a870-4401-8d18-d2ac39aedcc6">

<img width="287" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/eaba2302-caea-4484-b15f-d5228591f541">

### Create ‘Recommended’ Column

As seen in the figure above, some columns contain ‘no’, ‘yes’ values, so I created a new column called ‘Recommended’ and moved the values there. 
The code below was also used to extract and move the specified values from Traveller_type, Route and Flying_month columns to Recommended column.

<img width="405" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/f7292a1a-f331-46e6-8838-5dffbdceca05">

<img width="408" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/7e508921-b6fc-49fe-bc9f-25e07f6e416b">

<img width="428" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/ebd27766-5ada-49cd-a661-c410dd268a21">

### Moving Dates to Flying_month Column
The route column in the figure below contains some dates that should be in flying_month so I extracted and moved them below:

<img width="323" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/337319a7-a0b4-4e92-b29c-cff0a7e7898a">

<img width="318" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/1efa03de-9bc2-43d0-ad99-0674db53d50f">

<img width="321" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/ef597bc2-a9e8-4ea1-a63e-2fb3fdcc0cd9">

### Extracting Traveller_type Values from Class
Traveller_type values such as Solo leisure and Couple leisure were extracted from Class column and moved to traveller_type column below.

<img width="268" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/c76c5bff-dc1a-4c6c-9b04-f9c243e3b188">

### Extracting Route Values from Class

As seen in the figure above, class column contains Route values such as ‘London to Malaga’ and ‘LHR to ORD’. These were identified by ‘to’ separators and moved to their respective Route cells.

<img width="371" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/abd3eba8-2384-4502-8d92-3e4b44177226">

### Extracting Class values from Traveller_type Column

As seen below, Traveller_type column contains Class values such as ‘Business Class’ and ‘Economy Class’, so I moved them to Class.

<img width="346" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/54c01340-531a-4164-9c06-9555da634751">

### Extract Class values from Route Column

As seen in the figure below, Route column contains Class values such as ‘Economy Class’, so I moved them to Class.

<img width="337" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/1e2daf7b-7744-47ad-bb14-0563bf56aaaa">

<img width="330" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/c4c564c8-184f-448b-8d16-b97acb2df729">

<img width="326" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/b6ea19d3-c8e2-41c5-bf78-a80c45f33d1c">

Economy class has been moved to Class column.


### Extract Route values from Flying_month

As seen in the figure below, Flying_month column contains Route values such as ‘Miami to London, so I moved them to Route column.

<img width="383" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/257b0428-0ce3-4ba8-882c-86e3f2d9c214">

<img width="391" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/576f83ed-9d06-4de3-aa37-026a666ea315">

<img width="407" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/ebb788df-bc27-402a-bad1-8a601139dd86">

### Text Analysis: Extract Verified Status from Reviews

As seen in the figure below, the review_content column contains relevant information regarding verified status, travel date and travel route. These were extracted and moved to their respective columns.

<img width="375" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/6cdb0d84-4939-44f7-bed6-0461aa2b85ac">

<img width="367" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/dedaa3ef-5bea-43d7-94f7-af121778387f">

<img width="364" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/ef953a88-1303-4312-8487-82b8cacbe7ec">

Verified status was successfully extracted from reviews and updated in Verified column.

### Text Analysis: Extract Routes from Reviews

As seen in figure 19 below, Review_content contains relevant travel route information, so I extracted them using a REGEX function. This function identified various patterns matching airport codes and routes such as ‘LHR-LGW’, ‘LHR to LGW’, ‘Madrid to London’.

<img width="437" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/e196f0ef-8013-4fde-a03b-3abf4acdff05">

<img width="432" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/973ee2b2-4dcd-435f-8fa7-2150d4c3ff57">

<img width="426" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/632f0c2e-1892-40f9-bbf5-c189fc238e5c">

As seen in the figure below, travel routes were successfully extracted from review_content and moved to a new column called Travel_route.

### Standardization of Route Column

To ensure consistency across the route column, I used IATA (International Air Transport Association) mapping as a guide to decode airport codes into city names for easier analysis.
Since I am only interested in origin and destination cities for this analysis, I deleted transit cities. 

<img width="451" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/21c9f400-3cd7-4551-9755-7beeb8028c25">

<img width="451" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/6d996ece-3b1d-4176-9e82-be2c2c0bedbc">

<img width="451" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/ea41658b-e85f-440d-ba41-af77fe8b611f">

As seen above, ‘GLA to LHR’ was successfully changed to ‘Glasgow to London’.

### Splitting Route Column

I split Travel_Route column into Origin_City and Destination_City because I wanted to evaluate the popular destinations in this research project. Similar locations were renamed/grouped as one. For example, London city, Heathrow, Gatwick were renamed to ‘London’ for easier analysis and comparison. The new columns are seen in the figure below.

<img width="307" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/c32c8b30-a9e5-4e3e-abbe-ac83b262cac1">

<img width="307" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/91b85eb2-1ef5-418e-a955-c36662f6a39f">

<img width="402" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/260d80c1-15b0-460d-a8f3-4ddc0287f231">

### Text Analysis: Parsing Dates from Reviews

Various date formats were parsed from reviews and moved to a newly formed column called Formatted_Dates. As seen in figure 24 below, flying_month cell is missing because it is in review_content.

<img width="388" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/91309d52-4d14-4378-a47e-ae6d0797f965">
<img width="375" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/d8df7a50-51f6-4640-9201-94985bc0b8b4">
<img width="378" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/a106d67c-66bd-435a-af3a-f65920af58f0">

As seen above, date was successfully parsed in Mon-YY format and moved to new column (Formatted_Dates). I updated flying_month column with the dates and split it into Travel_Month and Travel_Year for easier analysis and comparison.

<img width="388" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/5d242513-3fff-43dd-a889-ed5d434b2755">

<img width="379" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/a8d9bea9-8a03-43e2-bc9b-7fa43c927b56">

## 4.3. Missing Values

Now that all the values are in their correct columns, we can proceed with handling missing values in the dataset. Missing values can introduce bias in statistical analysis and skew results, so by handling them, I can ensure that conclusions are based on a complete and representative dataset.

<img width="204" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/1ad0655b-0c4f-4e6d-a081-d62f2be60643">

### Data Imputation in ‘Rating’ Column

There are only 5 missing values in ‘Rating’ column, so I imputed with the highest occurring rating. As seen in the figure below, the highest occurring rating is 1 with over 800 reviews, so I replaced the missing (NaN) values with 1.

<img width="417" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/18aa341a-f2b0-4cb0-825f-1c00d447b5c6">
<img width="365" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/4f95bebb-8261-4f47-980b-3069787230bd">
<img width="380" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/9829577b-fe96-4ee0-9bd6-584cb24413d2">

As seen in the array above, there are no NaN values.

### Data Imputation in ‘Recommended’ Column

The ‘Recommended’ column has 2804 missing values and I imputed them by using ratings as a guide. Figure 31 below reveals that most reviewers who rated 1-5 will recommend the airline, while most reviewers who rated 6-10 will not recommend the airline. 

<img width="343" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/3ff1ee8e-8c7a-4cba-9406-50f183866da8">

<img width="361" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/91f6b3e7-c048-4793-9569-ef58f9a4a23c">
<img width="338" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/57ecc645-a45e-4e4b-b754-d800ee27a95e">

As seen in the figure above, I imputed missing values by assigning ‘no’ to ratings of 1-5 and assigned ‘yes’ to ratings of 6-10. There are now 0 missing values in Recommended column.

### Data Imputation in Travel_Month and Travel_Year

There are 2481 missing values in Travel_Month and Travel_Year columns. They were imputed using the backfill method where missing values are filled with the most recent past date along the same axis. I used this method of imputation because the entire dataset was grouped by dates in descending order. The review in row 1 was provided in 2023, while the review in row 3580 was provided in 2012.

<img width="380" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/8d3e4719-327b-4a68-825f-dc00ee2b5ad5">

<img width="137" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/695e02f8-3d82-4ecd-92d2-3d64ce17f5e7">

As seen in the figure above, there are no missing values in Rating, Class, Recommended, Travel_Month and Travel_Year. Verified column has missing values but it is not relevant in this analysis and will be deleted. The missing values in Traveller_type column were left in the dataset because the frequencies of top occurring traveller_type were relatively close as seen below.

<img width="300" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/3428a02d-4289-4d32-951e-10cabcc23477">

## 4.4. Delete Irrelevant Columns

<img width="451" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/2384f60f-ef19-4e8e-8140-64fe2fa009ff">

## 4.5. Clean Dataset

Data pre-processing is complete, and the clean dataset sample is seen below.

<img width="305" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/3ae1a6ad-e4eb-4fb9-b730-17f565e230a9">


# 5. Exploratory Data Analysis

## 5.1. Distribution of Ratings

<img width="319" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/8ca778f7-9e03-4b5e-94d9-85e9d5aac2d3">

The most frequent rating is 1, which indicates that the overall satisfaction level among passengers is very low.  Passengers are not satisfied with the airline’s service and their overall travel experience.

## 5.2.	Rating vs Class

I created a new column below called Rating_Desc which groups ratings into Low, Average and Good. Then I plotted a chart to view the distribution of reviews across all airline classes.

<img width="319" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/3aceae4c-6d36-426d-bad7-f6741a0064c3">
<img width="319" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/bc42a140-690c-477f-8c66-f7a03b45f343">
<img width="225" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/afbbd690-eb51-4e38-b02d-4249c55d7796"> <img width="216" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/27c2f2c4-b1a8-4264-be4d-755d210b068c">


Upon further investigation, low ratings are still dominant across all airline classes. However, relative to other classes, passengers in Economy class provided the most ‘lowest’ ratings, indicating a lack of overall satisfaction among economy passengers

## 5.3.	Rating vs Traveller_type

As seen above, low ratings are dominant across all traveller types, especially couples travelling for leisure. The chart also reveals that majority of passengers do not recommend the airline or travel experience. 

<img width="300" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/26e6df05-9adc-4f58-b768-7ffd22781fc4"> 
<img width="169" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/248d9e0d-81f8-4bb5-bc00-277129c009d8"> <img width="155" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/efa714d1-d134-442f-ad97-21835ed1b87c">

## 5.4.	Distribution of Ratings by Travel Destinations

Relative to other destinations, flights to London have the most positive and most negative reviews.

<img width="311" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/a8b4c1ed-48b9-4a83-9d28-e7cc229f684f"> <img width="214" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/b16956c3-3b82-4243-b95d-130eb84166b3"> <img width="211" alt="image" src="https://github.com/kelechiu/Applying-Big-Data-Analytics-to-Airline-Reviews/assets/100145388/4cd5ab53-c9c6-4c87-a5d1-eef77eee824b">


## 5.5.	Sentiment Analysis

Sentiment analysis was conducted to evaluate the range of emotions conveyed in the airline reviews and understand how customers feel about their travel experience. Sentiments were grouped as either positive or negative, and as seen in figure below, the emotions conveyed in the reviews were mostly positive.

