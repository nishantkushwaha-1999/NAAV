# Exercises

##### Group Members: 
1. Akash Goyal (ag84248)
2. Nishant Singh (nsk779)
3. Vaibhav Nagar (vn5339)
4. Ambarish Narayan (an32967)

# Probability Practice

### Part (a)

Visitors to your website are asked to answer a single survey question before they get access to the content on the page. Among all of the users, there are two categories: Random Clicker (RC), and Truthful Clicker (TC). There are two possible answers to the survey: yes and no. Random clickers would click either one with equal probability. You are also giving the information that the expected fraction of random clickers is 0.3. After a trial period, you get the following survey results: 65% said Yes and 35% said No. What fraction of people who are truthful clickers answered yes? Hint: use the rule of total probability.

### Answer

Let's denote the events:

Event A: User is a Random Clicker (RC)

Event T: User is a Truthful Clicker (TC)

Event Y: User's answer is "Yes"

Event N: User's answer is "No"

We are given:

P(A) = 0.3 (expected fraction of random clickers)

P(T) = 1 - P(A) = 0.7 (fraction of truthful clickers)

P(Y\|A) = 0.5 (random clickers would click "Yes" with equal probability)

P(N\|A) = 0.5 (random clickers would click "No" with equal probability)

P(Y\|T) = ? (fraction of truthful clickers who answered "Yes")

P(N\|T) = 1 - P(Y\|T) = ? (fraction of truthful clickers who answered "No")

We want to find P(Y\|T), which is the fraction of truthful clickers who answered "Yes."

Using the law of total probability:

P(Y) = P(A) \* P(Y\|A) + P(T) \* P(Y\|T)

Substitute the known values:

0.65 = 0.3 \* 0.5 + 0.7 \* P(Y\|T)

Now solve for P(Y\|T):

0.65 = 0.15 + 0.7 \* P(Y\|T)

P(Y\|T) = 0.7143

Therefore, the fraction of people who are truthful clickers and answered "Yes" is approximately 0.7143 or 71.43%.

### Part (b)

Imagine a medical test for a disease with the following two attributes:

-   The sensitivity is about 0.993. That is, if someone has the disease, there is a probability of 0.993 that they will test positive.

-   The specificity is about 0.9999. This means that if someone doesn't have the disease, there is probability of 0.9999 that they will test negative.

-   In the general population, incidence of the disease is reasonably rare: about 0.0025% of all people have it (or 0.000025 as a decimal probability).

Suppose someone tests positive. What is the probability that they have the disease?

### Answer
This is a classic application of Bayes' theorem, which can help us calculate the probability that someone actually has the disease given that they tested positive. Let's denote the events:

-   Event D: Person has the disease.

-   Event P: Person tests positive.

We are given the following probabilities:

-   P(D) = 0.000025 (probability of having the disease)

-   P(!D) = 1 - P(D) = 1 - 0.000025 = 0.999975 (probability of not having the disease)

-   P(P\|D) = 0.993 (probability of testing positive given that the person has the disease)

-   P(P\|!D) = 1 - specificity = 1 - 0.9999 = 0.0001 (probability of testing positive given that the person does not have the disease)

We want to find P(D\|P), which is the probability that someone has the disease given that they tested positive.

Using Bayes' theorem:

P(D\|P) = (P(P\|D) \* P(D)) / P(P)

The denominator, P(P), can be calculated using the law of total probability:

P(P) = P(P\|D) \* P(D) + P(P\|!D) \* P(!D)

Now substitute the values and calculate:

P(P) = (0.993 \* 0.000025) + (0.0001 \* 0.999975) ≈ 0.0001249

P(D\|P) = (0.993 \* 0.000025) / 0.0001249 ≈ 0.1995

Therefore, the probability that someone who tests positive actually has the disease is approximately 0.1995 or 19.95%. Despite the high sensitivity and specificity of the test, due to the rarity of the disease in the general population, the positive predictive value is relatively low.

# Wrangling the Billboard Top 100

Consider the data in [billboard.csv](https://github.com/jgscott/STA380/blob/bd4000b1d6146fc4137e76a110b7c2d3f8951e27/data/billboard.csv) containing every song to appear on the weekly [Billboard Top 100](https://www.billboard.com/charts/hot-100/) chart since 1958, up through the middle of 2021. Each row of this data corresponds to a single song in a single week. For our purposes, the relevant columns here are:

-   performer: who performed the song

-   song: the title of the song

-   year: year (1958 to 2021)

-   week: chart week of that year (1, 2, etc)

-   week_position: what position that song occupied that week on the Billboard top 100 chart.

Use your skills in data wrangling and plotting to answer the following three questions.

[code](https://github.com/mostwanted-786/NAAV/blob/main/02_Wrangling%20the%20Billboard%20Top%20100/Wrangling%20the%20Billboard%20Top%20100.ipynb)

### Part (a)

Make a table of the top 10 most popular songs since 1958, as measured by the *total number of weeks that a song spent on the Billboard Top 100.* Note that these data end in week 22 of 2021, so the most popular songs of 2021 will not have up-to-the-minute data; please send our apologies to The Weeknd.

Your table should have **10 rows** and **3 columns**: `performer`, `song`, and `count`, where `count` represents the number of weeks that song appeared in the Billboard Top 100. Make sure the entries are sorted in descending order of the `count` variable, so that the more popular songs appear at the top of the table. Give your table a short caption describing what is shown in the table.

(*Note*: you'll want to use both `performer` and `song` in any `group_by` operations, to account for the fact that multiple unique songs can share the same title.)

### Answer
![image](https://github.com/mostwanted-786/NAAV/assets/137720186/d81026d2-741d-442e-abeb-b97444227e8c)

### Part (b)

Is the "musical diversity" of the Billboard Top 100 changing over time? Let's find out. We'll measure the musical diversity of given year as *the number of unique songs that appeared in the Billboard Top 100 that year.* Make a line graph that plots this measure of musical diversity over the years. The x axis should show the year, while the y axis should show the number of unique songs appearing at any position on the Billboard Top 100 chart in any week that year. For this part, please filter the data set so that it excludes the years 1958 and 2021, since we do not have complete data on either of those years. Give the figure an informative caption in which you explain what is shown in the figure and comment on any interesting trends you see.

There are number of ways to accomplish the data wrangling here. For example, you could use two distinct sets of data-wrangling steps. The first set of steps would get you a table that counts the number of times that a given song appears on the Top 100 in a given year. The second set of steps operate on the result of the first set of steps; it would count the number of unique songs that appeared on the Top 100 in each year, *irrespective of how many times* it had appeared.

### Answer
![image](https://github.com/mostwanted-786/NAAV/assets/137720186/9442d0a6-2d29-4fc2-8bb0-d0257dc825f8)

### Part (c)

Let's define a "ten-week hit" as a single song that appeared on the Billboard Top 100 for at least ten weeks. There are 19 artists in U.S. musical history since 1958 who have had *at least 30 songs* that were "ten-week hits." Make a bar plot for these 19 artists, showing how many ten-week hits each one had in their musical career. Give the plot an informative caption in which you explain what is shown.

*Notes*:

1.  You might find this easier to accomplish in two distinct sets of data wrangling steps.

2.  Make sure that the individuals names of the artists are readable in your plot, and that they're not all jumbled together. If you find that your plot isn't readable with vertical bars, you can add a `coord_flip()` layer to your plot to make the bars (and labels) run horizontally instead.

3.  By default a bar plot will order the artists in alphabetical order. This is acceptable to turn in. But if you'd like to order them according to some other variable, you can use the `fct_reorder` function, described in [this blog post](https://datavizpyr.com/re-ordering-bars-in-barplot-in-r/). This is optional.

### Answer
![image](https://github.com/mostwanted-786/NAAV/assets/137720186/b1cdb433-32eb-40fe-a199-db2cef63a47d)


# Visual story telling part 1: green buildings

### Question: 
Do you agree with the conclusions of her on-staff stats guru? If so, point to evidence supporting his case. If not, explain specifically where and why the analysis goes wrong, and how it can be improved. Do you see the possibility of confounding variables for the relationship between rent and green status? If so, provide evidence for confounding, and see if you can also make a picture that visually shows how we might "adjust" for such a confounder. Tell your story in pictures, with appropriate introductory and supporting text.

### Solution:
### [Code](https://github.com/mostwanted-786/NAAV/blob/main/03_Visual_%20story_telling%20part1_green_buildings/Visual_story_telling_part%20_Green_Buildings.ipynb)
In order to understand and verify the conclusions drawn by the Excel guru, I created several charts to explore various aspects:

### Low Occupancy Rates:

![newplot](https://github.com/mostwanted-786/NAAV/assets/139088219/cdc65498-60e1-4dac-96ac-d5c7e812bde6)

![newplot-2](https://github.com/mostwanted-786/NAAV/assets/139088219/6a8f6d36-8bd6-48ff-8eb9-412e33688a2c)

The above two charts reveal a skewness in the data, with the majority of data points indicating over 50% occupancy. Consequently, the decision to remove low occupancy rates appears reasonable.

### Agreement with Excel Guru's Conclusion:
While I concur with the Excel guru's conclusion, the calculations indicate that profits from a green building are expected after 8.5 years. Given that the average building age is approximately 47 years, the investment in a green building is evidently profitable over the long term.


### Additional Factors to Consider:
In order to make a well-informed decision, it is essential to consider other influencing factors. I explored these aspects with the following visualizations:

### Green Rating vs. Rent:
![Screenshot 2023-08-14 at 1 56 39 AM](https://github.com/mostwanted-786/NAAV/assets/139088219/8b1f9808-0000-41ac-88e5-14dae79e71b6)

The median rent is higher for buildings with a Green Rating of 1, indicating a potential positive impact on rent from having green certification (+0.18$)


### Leasing Rate vs Rent:
![image](https://github.com/mostwanted-786/NAAV/assets/139088219/dff0aef2-05cb-4d83-ba31-e9849115524b)

As expected, there is a correlation between higher leasing rates or occupancy and increased rent

### Stories vs. Rent: 

![newplot-5](https://github.com/mostwanted-786/NAAV/assets/139088219/067b8872-a2ba-4d3e-ba79-b387f64ef1b5)

Lower floor or stories tend to command higher rents compared to higher floor buildings

### Amenities vs. Rent: 
![newplot-8](https://github.com/mostwanted-786/NAAV/assets/139088219/4d2d8d9d-4f0c-4a1b-acf6-ec4e14b48ac7)

![image](https://github.com/mostwanted-786/NAAV/assets/139088219/07ec3095-2f39-4af9-9dbf-adea4ad7ea58)

Interestingly, the presence of amenities does not appear to significantly impact higher rents.

### Quality(class a,b) vs. Rent: 
![newplot-13](https://github.com/mostwanted-786/NAAV/assets/139088219/9a8b2149-f4e0-4663-9521-4317742f1c52)

![newplot-14](https://github.com/mostwanted-786/NAAV/assets/139088219/a77cd59e-67b2-49dc-a759-b9b3d0ead921)

The quality classes (Class A and B) also do not seem to play a significant role in obtaining higher rents for green buildings

These visualizations help us understand how the the developer can make a better decision in order to to understand the potential confounding factors that might affect the relationship between green status and rent.

### Conclusion: Adjusting for Confounds
Taking into account the preliminary analysis and the insights gained from the visualizations, it is reasonable to consider building a green building as financially viable. However, to maximize the benefits, attention must be given to potential confounding factors. Constructing buildings with lower floors, a focus on occupancy rates, and less emphasis on amenities could lead to better rent outcomes.


# Visual Story Telling Part 2

### Question:
Your task is to create a figure, or set of related figures, that tell an interesting story about Capital Metro ridership patterns around the UT-Austin campus during the semester in question. Provide a clear annotation/caption for each figure, but the figure(s) should be more or less stand-alone, in that you shouldn't need many, many paragraphs to convey its meaning. 
Rather, the figure together with a concise caption should speak for itself as far as possible.

### Solution:
### [Code](https://github.com/mostwanted-786/NAAV/blob/main/04_Visual%20story%20telling%20part%202Capital%20Metro%20data/Visual_story_telling_Capital_Metro_data.ipynb)
Effective storytelling often involves the creation of insightful visualizations. Here are the key visualizations for the Capital Metro ridership data around the UT-Austin campus during the semester:

#### Ridership Distribution by Weekend and Weekday:
![newplot-26](https://github.com/mostwanted-786/NAAV/assets/139088219/c27a4c28-4ae4-4d78-a91c-dbd9e41fcd54)


![newplot-16](https://github.com/mostwanted-786/NAAV/assets/139088219/998d6233-b5a2-4e63-ba31-614e903b2d2b)

##### It is evident that weekdays exhibit significantly higher ridership compared to weekends.


#### Correlation matrix:
![newplot-25](https://github.com/mostwanted-786/NAAV/assets/139088219/59f0f8fe-7eed-423e-be43-53e546c83730)

A correlation matrix generated to discern the variables' impact on boarding. The following correlations observed:
boarding       1.000000

hour_of_day    0.351907

temperature    0.197585

alighting      0.120225

#### hour_of_day is one of the most important variable

Further exploration directed towards understanding the relationship between hour of day and ridership.
#### Average Boarding Ridership by Hour and Day Heatmap:

![newplot-18](https://github.com/mostwanted-786/NAAV/assets/139088219/68d07e66-8e68-445f-8ea1-2e4daa484dd9)

The heatmap aboe underlines that 3pm-5pm on weekdays witnesses the highest ridership levels.

#### Ridership Distribution by Weekend and Weekday by hour of day:
![newplot-31](https://github.com/mostwanted-786/NAAV/assets/139088219/e51d4a46-aeae-4335-89f6-35ec1dd5992e)

![newplot-30](https://github.com/mostwanted-786/NAAV/assets/139088219/56277bef-3a73-4184-9698-0cea065383d5)

![newplot-35](https://github.com/mostwanted-786/NAAV/assets/139088219/a56047d0-4b34-4093-9fbe-7ab5bded87fc)

Weekdays: Peak hours consistently fall around 4pm, except for Thursdays, where it occurs around 3pm.

Weekends: Saturdays witness peak ridership at around 10am, while Sundays continue to maintain their usual peak hours between 4-5pm.

#### Average Boarding Ridership by Month for hour of day:

![newplot-29](https://github.com/mostwanted-786/NAAV/assets/139088219/564a6cf0-4107-4cf5-b36b-df8fe35a6cee)

This visualization, portraying ridership across months, fails to reveal significant spikes or drops. Subsequent charts consider temperature variations for better insights.

#### Average Boarding Ridership Trend by Hour of Day for each day of week: 

![newplot-27](https://github.com/mostwanted-786/NAAV/assets/139088219/4b578b22-0115-4014-9ac0-1cac52229065)

 
This indicated that during these months, how each day observed ridership on average. It's a valuable tool to cater to specific daily demands.

#### Average Boarding Ridership Trend by Hour of Day for each month as well as temperature: 

![newplot-34](https://github.com/mostwanted-786/NAAV/assets/139088219/f3f77988-8c92-41a9-889d-2ce5b7e71f60)

This intricate chart maps ridership trends for specific hours across different months. It uncovers changes as the semester unfolds, influenced by temperature variations. Notably, it also exposes distinct patterns between weekends and weekdays, with noticeable dips during weekends. For November, unusual ridership patterns around hour 12 and 18 in the second-last week are visible.
 
### Summary:

### Weekdays are Busier: 
Weekdays experience significantly higher ridership compared to weekends. This suggests that the transit service is more frequently used by students and faculty during academic days.

### Hour of Day Matters: 
The hour of the day plays a crucial role in ridership. Peak hours are observed around 3pm-5pm on weekdays, indicating the time when students are likely to commute to and from the campus.

### Month and Temperature Impact: 
While no significant spikes or drops in ridership are observed across months, the average ridership trend by month indicates a consistent pattern. The temperature variations are also considered to identify how ridership changes with weather conditions.

### Day-to-Day Variation: 
The line plot showcasing the average boarding ridership trend by hour of the day for each day of the week provides a day-to-day understanding of the ridership. This information can help optimize transit services based on daily demand.

### Weekend vs. Weekdays: 
The last chart demonstrates the ridership trend over different months and hours of the day, showcasing a clear pattern between weekends and weekdays. It's evident that weekends experience sudden drops in ridership, while weekdays follow a more consistent trend.

### From these visualizations, it's evident that understanding the factors influencing ridership is essential for effective transportation management. By identifying peak hours, analyzing monthly variations, and considering weather conditions, Capital Metro can make informed decisions to improve services and cater to the needs of its riders.

### Conclusion:
In conclusion, by harnessing the insights derived from this data-driven visual storytelling, Capital Metro can enhance its services, optimize routes, and provide a more efficient and convenient transportation experience for the UT-Austin community.

# Clustering and Dimensionality
The data in wine.csv contains information on 11 chemical properties of 6500 different bottles of vinho verde wine from northern Portugal. In addition, two other variables about each wine are recorded:
-   Whether the wine is red or white
-   The quality of the wine, as judged on a 1-10 scale by a panel of certified wine snobs.

Run PCA, tSNE, and any clustering algorithm of your choice on the 11 chemical properties (or suitable transformations thereof) and summarize your results. Which dimensionality reduction technique makes the most sense to you for this data? Convince yourself (and me) that your chosen approach is easily capable of distinguishing the reds from the whites, using only the "unsupervised" information contained in the data on chemical properties. Does your unsupervised technique also seem capable of distinguishing the higher from the lower-quality wines? Present appropriate numerical and/or visual evidence to support your conclusions.

To clarify: I'm not asking you to run a supervised learning algorithm. Rather, I'm asking you to see whether the differences in the labels (red/white and quality score) emerge naturally from applying an unsupervised technique to the chemical properties. This should be straightforward to assess using plots.

### Answer

### [Code](https://github.com/mostwanted-786/NAAV/blob/main/05_Clustering%20and%20Dimensionality%20Reduction/Clustering%20and%20Dimensionality%20Reduction.ipynb)

#### PCA | Wine Color Clustering                                                  
![PCA Output-1](https://github.com/mostwanted-786/NAAV/assets/32060433/8bcdbb20-2822-43ef-af11-33353ab73561)
#### tSNE | Wine Color Clustering   
![tSNE Output -1](https://github.com/mostwanted-786/NAAV/assets/32060433/02589b2f-e123-477e-91e3-ff26b3fb9b65)

Looking at the plots on actual vs predicted for wine color as well as the model accuracy it is evident that PCA is a better dimensionality reduction technique for this dataset. A Kmeans algorithm on data after PCA with just 2 variables is doing far better job (better accuracy) than that from tSNE.

#### PCA | Wine Quality Clustering   
![PCA Output -2](https://github.com/mostwanted-786/NAAV/assets/32060433/087ad1ae-96b4-4c56-a84f-9ee19a2e5475)
#### tSNE | Wine Quality Clustering 
![tSNE Output -2](https://github.com/mostwanted-786/NAAV/assets/32060433/0b44ff8f-bf26-49b2-b064-b3f3633a4561)

The actual vs predictions plot made on wine quality using clustering tells us that both the techniques are not able to distinguish between the qualities of wines.

# Market Segmentation
Consider the data in social_marketing.csv. This was data collected in the course of a market-research study using followers of the Twitter account of a large consumer brand that shall remain nameless---let's call it "NutrientH20" just to have a label. The goal here was for NutrientH20 to understand its social-media audience a little bit better, so that it could hone its messaging a little more sharply.

A bit of background on the data collection: the advertising firm who runs NutrientH20's online-advertising campaigns took a sample of the brand's Twitter followers. They collected every Twitter post ("tweet") by each of those followers over a seven-day period in June 2014. Every post was examined by a human annotator contracted through Amazon's Mechanical Turk service. Each tweet was categorized based on its content using a pre-specified scheme of 36 different categories, each representing a broad area of interest (e.g. politics, sports, family, etc.) Annotators were allowed to classify a post as belonging to more than one category. For example, a hypothetical post such as "I'm really excited to see grandpa go wreck shop in his geriatic soccer league this Sunday!" might be categorized as both "family" and "sports." You get the picture.

Each row of social_marketing.csv represents one user, labeled by a random (anonymous, unique) 9-digit alphanumeric code. Each column represents an interest, which are labeled along the top of the data file. The entries are the number of posts by a given user that fell into the given category. Two interests of note here are "spam" (i.e. unsolicited advertising) and "adult" (posts that are pornographic, salacious, or explicitly sexual). There are a lot of spam and pornography "bots" on Twitter; while these have been filtered out of the data set to some extent, there will certainly be some that slip through. There's also an "uncategorized" label. Annotators were told to use this sparingly, but it's there to capture posts that don't fit at all into any of the listed interest categories. (A lot of annotators may used the "chatter" category for this as well.) Keep in mind as you examine the data that you cannot expect perfect annotations of all posts. Some annotators might have simply been asleep at the wheel some, or even all, of the time! Thus there is some inevitable error and noisiness in the annotation process.

Your task to is analyze this data as you see fit, and to prepare a concise report for NutrientH20 that identifies any interesting market segments that appear to stand out in their social-media audience. You have complete freedom in deciding how to pre-process the data and how to define "market segment." (Is it a group of correlated interests? A cluster? A latent factor? Etc.) Just use the data to come up with some interesting, well-supported insights about the audience, and be clear about what you did.

### Answer

### [Code](https://github.com/mostwanted-786/NAAV/blob/main/06_Market%20segmentation/Market%20Segmentation.ipynb)

In the effort to create customer segments we did a dimensionality reduction exercise using PCA and then created customer cohorts using both Kmeans ++ and hierarchical clustering. We created 13 cohorts in the begining to start with, based on the elbow curve and the dendrogram respectively. For both the models 13 clusters looked like the optimum number. Customers in each cluster was then profiled to get the insights into the cluster. Since KMeans was giving much better defined clusters in our sense we went ahead with it. Furthermore, we decided to club some of the clusters having similar profiles of customers and finally have 10 clusters/segment of customers as below

Cluster 1:
![output1](https://github.com/mostwanted-786/NAAV/assets/32060433/4d15acfa-4e8a-44e0-9804-b6a84cd9db9b)
This comprises of people who are chatting with each other on twitter a lot. They also share details around what they are doing in their normal everyday life. This cohort is the biggest one in terms of the number


Cluster 2:
![output2](https://github.com/mostwanted-786/NAAV/assets/32060433/d89097f3-84b3-4958-a7ce-0e1394affe6a)
These are sports enthusiasts and highly active people. They are also into healthy fooding and cooking habits and post about in their twitter


Cluster 3:
![output3](https://github.com/mostwanted-786/NAAV/assets/32060433/b9474ee6-a7e7-4a88-8c5b-3497de56b4b4)
This comprises of people who are art enthusiasts and watch movies. We believe that these are people who use the product during movies or possibly art exhibitions as refreshment


Cluster 4:
![output4](https://github.com/mostwanted-786/NAAV/assets/32060433/f606f00e-310f-495d-adff-39c6b0d625f6)
This cohort comprised of mostly college going adults who are also very much into gaming


Cluster 5:
![output5](https://github.com/mostwanted-786/NAAV/assets/32060433/f5079049-bfe4-4546-90d4-ec774691a52b)
In this cluster we believe we have family oriented and religious people who are talking about food, parenting,school etc


Cluster 6:
![output6](https://github.com/mostwanted-786/NAAV/assets/32060433/1ae08997-ac78-427a-a281-3fdaedd5e8d9)
This cohort comprises of people with posts that are pornographic, salacious, or explicitly sexual. Also, this is the smallest of all cohorts in terms of population.


Cluster 7:
![output7](https://github.com/mostwanted-786/NAAV/assets/32060433/b84c4c82-ef64-4de8-9324-1fd80d8a0e1a)
The cohort comprises of people who are more into cooking, photo sharing, fashion and beauty. We hypothesise that these are mostly women


Cluster 8:
![output8](https://github.com/mostwanted-786/NAAV/assets/32060433/9bb7001b-d672-48f6-8e96-2f5d1ae76108)
The cohort comprises of people who talking about news, politics, automotives and sports. This could be a pool of mature adults who are into car/ bike racing sports


Cluster 9:
![output9](https://github.com/mostwanted-786/NAAV/assets/32060433/391b4aa4-338e-4ae4-8b59-690014967d76)
The cohort comprises of people who talking about politics and travel



# Reuters Corpus

Revisit the Reuters C50 text corpus that we briefly explored in class. Your task is simple: tell an interesting story, anchored in some analytical tools we have learned in this class, using this data. For example:

* you could cluster authors or documents and tell a story about what you find.
* you could look for common factors using PCA.
* you could train a predictive model and assess its accuracy, constructing features for each document that maximize performance.
* you could do anything else that strikes you as interesting with this data.

Describe clearly what question you are trying to answer, what models you are using, how you pre-processed the data, and so forth. Make sure you include at least one really interesting plot (although more than one might be necessary, depending on your question and approach.)

Format your write-up in the following sections, some of which might be quite short:

* Question: What question(s) are you trying to answer?
* Approach: What approach/statistical tool did you use to answer the questions?
* Results: What evidence/results did your approach provide to answer the questions? (E.g. any numbers, tables, figures as appropriate.)
* Conclusion: What are your conclusions about your questions? Provide a written interpretation of your results, understandable to stakeholders who might plausibly take an interest in this data set.

Regarding the data itself: In the C50train directory, you have 50 articles from each of 50 different authors (one author per directory). Then in the C50test directory, you have another 50 articles from each of those same 50 authors (again, one author per directory). This train/test split is obviously intended for building predictive models, but to repeat, you need not do that on this problem. You can tell any story you want using any methods you want. Just make it compelling!

Note: if you try to build a predictive model, you will need to figure out a way to deal with words in the test set that you never saw in the training set. This is a nontrivial aspect of the modeling exercise. (E.g. you might simply ignore those new words.)

This question will be graded according to three criteria:

1. the overall "interesting-ness" of your question and analysis.
2. the clarity of your description. We will be asking ourselves: could your analysis be reproduced by a competent data scientist based on what you've said? (That's good.) Or would that person have to wade into the code in order to understand what, precisely, you've done? (That's bad.)
3. technical correctness (i.e. did you make any mistakes in execution or interpretation?)


### Answer

* Question: Identify topics from the text data and summarize your findings.

* Approach: We utilized Latent Dirichlet Allocation (LDA), a generative probabilistic model, to extract the most important topics from the training data. LDA works by assuming that each document in the corpus is a mixture of a small number of topics and that each word's presence is attributable to one of the document's topics. We then identified the most prevalent topic in the test set files ([analysis notebook](https://github.com/mostwanted-786/NAAV/blob/main/07_Reuters%20Corpus/Reuters.ipynb)).

* Results: Some of the topics that were identified through LDA were:

| Topic    | Keywords                                                                                       | Class                                     |
|----------|:----------------------------------------------------------------------------------------------:|------------------------------------------:|
| Topic 1  | united, states, trade, said, drug, china, ban, department, colombia, congress                  | International Trade                       |
| Topic 2  | hong, kong, china, said, tung, chinese, people, territory, rule, says                          | Hong Kong-China Relations                 |
| Topic 3  | internet, corp, new, computer, said, software, technology, microsoft, network, services        | Technology and Software                   |
| Topic 4  | said, financial, chairman, president, statement, company, vice, board, right, street           | Corporate Leadership and Governance       |
| Topic 5  | amp, local, long, market, competition, service, phone, cable, rules, companies                 | Telecommunications and Market Competition |
| Topic 6  | told, reuters, director, interview, reporters, quality, telephone, areas, conference, managing | Media and Communication                   |
| Topic 7  | china, said, beijing, chinese, official, taiwan, officials, economic, communist, state         | Chinese Economy and Policy                |
| Topic 8  | news, said, early, fund, 1997, joint, year, venture, start, 1998                               | News and Media Industry                   |
| Topic 9  | 000, tonnes, said, saying, 100, cocoa, year, copper, 500, figures                              | Commodity Markets                         |
| Topic 10 | percent, gold, price, said, share, market, 20, bre, 15, stocks                                 | Financial Markets and Investment          |
| Topic 11 | said, wang, court, rights, case, chinese, given, government, details, action                   | Human Rights and Legal Cases              |
| Topic 12 | chief, executive, said, company, years, officer, new, ago, development, chairman               | Business Leadership and Development       |
| Topic 13 | bank, banks, year, percent, rate, canada, central, credit, said, banking                       | Banking and Finance                       |
| Topic 14 | million, year, pounds, profit, profits, half, 1995, net, percent, 30                           | Financial Performance                     |
| Topic 15 | deal, company, largest, merger, world, mci, bt, british, stake, percent                        | Mergers and Acquisitions                  |
| Topic 16 | billion, year, total, debt, said, francs, worth, ve, percent, got                              | Financial Transactions and Debt           |
| Topic 17 | said, analyst, think, going, market, term, good, don, people, added                            | Market Analysis and Forecasting           |
| Topic 18 | quarter, sales, year, said, earnings, share, analysts, expected, results, company              | Corporate Earnings and Results            |
| Topic 19 | government, said, czech, general, minister, ahead, finance, party, house, ministry             | Government and Politics                   |
| Topic 20 | said, offer, shareholders, french, american, airbus, south, company, north, new                | Corporate Shares and Ownership            |
| Topic 21 | british, pence, bid, air, share, plc, group, said, dividend, britain                           | Stock Market and Investments              |
| Topic 22 | said, prices, oil, year, demand, russia, domestic, set, rates, export                          | Oil and Energy Markets                    |
| Topic 23 | business, said, life, insurance, japan, market, financial, non, group, banks                   | Business and Finance in Japan             |
| Topic 24 | gm, said, workers, plant, agreement, union, ford, car, plants, comment                         | Automotive Industry and Labor Relations   |
| Topic 25 | stock, shares, trading, exchange, new, close, york, points, share, toronto                     | Stock Market Trading and Exchanges        |

  After analyzing the test data files, it was found that topic 7 is the most prevalent topic in the test files.
  
  ![newplot](https://github.com/mostwanted-786/NAAV/assets/60353780/f0497b6e-03b5-4921-ba96-4e9c86e942a8)
  
  We also have a summary of the most frequent topics written by each of the writers.
  
  ![newplot](https://github.com/mostwanted-786/NAAV/assets/60353780/3286a6e3-1b06-496a-8848-5334ce588b58)

* Conclusion: We identified distinct topics, each characterized by a set of keywords that provided meaningful context. The results of our analysis showcased a diverse range of topics present in the dataset, from global trade and technology advancements to legal cases and economic developments.s. We conducted an analysis of the test data files and determined that topic 7, centered around economic and geopolitical issues in China, emerged as the most prevalent topic among the test articles. This finding emphasizes the significance of this particular theme within the writings of the authors, potentially highlighting their expertise and areas of interest.

# Association rule mining

Revisit the notes on association rule mining and the R example on music playlists: playlists.R and playlists.csv. Then use the data on grocery purchases in groceries.txt and find some interesting association rules for these shopping baskets. The data file is a list of shopping baskets: one person's basket for each row, with multiple items per row separated by commas. Pick your own thresholds for lift and confidence; just be clear what these thresholds are and say why you picked them. Do your discovered item sets make sense? Present your discoveries in an interesting and visually appealing way.

Notes:

* This is an exercise in visual and numerical story-telling. Do be clear in your description of what you've done, but keep the focus on the data, the figures, and the insights your analysis has drawn from the data, rather than technical details.
* The data file is a list of baskets: one row per basket, with multiple items per row separated by commas. You'll have to cobble together your own code for processing this into the format expected by the "arules" package. This is not intrinsically all that hard, but it is the kind of data-wrangling wrinkle you'll encounter frequently on real problems, where your software package expects data in one format and the data comes in a different format. Figuring out how to bridge that gap is part of the assignment, and so we won't be giving tips on this front.

### Answer

We analyzed the hidden relationships in the dataset given, which consists of baskets (i.e., items purchased in a shopping kart). The lift value of greater than 10 was selected, indicating a higher positive relation between the rules, and a confidence value of greater than 0.5, indicating a high likelihood of the relation. Also after hit and trial, these values provided 14 relations to analyze (refer to the [R file](https://github.com/mostwanted-786/NAAV/blob/main/08_Association%20Rule%20Mining/groceries.R) and [graph](https://github.com/mostwanted-786/NAAV/blob/main/08_Association%20Rule%20Mining/groceries.graphml)).

After looking at the rules we inferred a lot of exciting associations:
* People who buy liquor or red/blush wine tend to buy bottled beer as well, indicating that all the liquor sections should be located in close proximity.
* People who buy ham, cheese, or eggs also buy white bread. this indicates that all these items are related.
* People who buy baking powder and soda also buy sugar, maybe for baking a cake or something. If these items are located together then it will be easier for the people to grab the items.
* Root vegetables have a high lift value with other fruits and vegetables, so they can be placed together. This makes sense since most people shop for their vegetables and fruits together.

# Image classification with neural networks

In this problem, you will train a neural network to classify satellite images. In the data/EuroSAT_RGB directory, you will find 11 subdirectories, each corresponding to a different class of land or land use: e.g. industrial, crops, rivers, forest, etc. Within each subdirectory, you will find examples in .jpg format of each type. (Thus the name of the directory in which the image lives is the class label.)

Your job is to set up a neural network that can classify the images as accurately as possible. Use an 80/20 train test split. Summarize your model and its accuracy in any way you see fit, but make you include at a minimum the following elements:

overall test-set accuracy, measured however you think is appropriate
show some of the example images from the test set, together with your model's predicted classes.
a confusion matrix showing the performance of the model on the set test, i.e. a table that cross-tabulates each test set example by (actual class, predicted class).
I strongly recommend the use of PyTorch in a Jupyter notebook for this problem; look into PyTorch's ImageFolder data set class, which will streamline things considerably.

### Answer

The image data was trained with an 80/20 split between training and testing (refer to the [file](https://github.com/mostwanted-786/NAAV/blob/main/09_Image%20Classification/Image%20Classification.ipynb)). The following CNN was used to train the data:
* (conv1): Conv2d(3, 64, kernel_size=(3, 3), stride=(1, 1))
* (conv2): Conv2d(64, 128, kernel_size=(3, 3), stride=(1, 1))
* (conv3): Conv2d(128, 256, kernel_size=(3, 3), stride=(1, 1))
* (dropout1): Dropout(p=0.25, inplace=False)
* (dropout2): Dropout(p=0.5, inplace=False)
* (dropout3): Dropout(p=0.7, inplace=False)
* (fc1): Linear(in_features=215296, out_features=2048, bias=True)
* (fc3): Linear(in_features=2048, out_features=512, bias=True)
* (fc4): Linear(in_features=512, out_features=128, bias=True)
* (fc5): Linear(in_features=128, out_features=10, bias=True)

A sample prediction in the final stages of training is shown below:

![image](https://github.com/mostwanted-786/NAAV/assets/60353780/8a20134f-cfa5-49d9-baa4-0d07e7deea98)

Actual: 6 4 6 9 9 2 1 1
Predicted: 6 4 3 9 9 2 1 1

The final accuracy of the model is: ~94%

The confusion matrix on the test data is shown below:

![image](https://github.com/mostwanted-786/NAAV/assets/60353780/2bd11db8-bbaa-452c-b5ec-972f2339c838)

