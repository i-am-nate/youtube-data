# youtube-data
Analyzing YouTube channel data from Tabletop Sandbox (2.25.23-8.27.23)

**Tabletop Sandbox** is a channel on YouTube that belongs to Tabletop Sandbox LLC, a business launched with [the YouTube channel](http://youtube.com/@tabletopsandbox) on February 25, 2023; I claim part ownership in this company. On September 1, 2023, one of the fellow co-owners and I retrieved from YouTube data concerning the channel in order to answer some questions, all of which had to do with the underlying desire to increase viewership.

Apart from the first week (February 25) in which four videos released, every week thereafter one video released per week until the the final video in the period (August 27). In thinking through how the data could help increase overall viewership on the channel, four main questions rose to the surface that we wanted to answer: 1) How long are people sticking with each video? 2) How does the intro affect retention? 3) How does video length affect retention? and 4) Are there certain categories that perform better than others?

Much of the data we needed was contained within the YouTube Studio account, and so I downloaded a csv and imported it into Google Sheets ([see the document here](https://docs.google.com/spreadsheets/d/1YxjRCyv-KDdmIGukaEMBs8gkpunVQQ_qvd4I2frD_jI/edit#gid=7763040)).

The finished Google Sheets document is laid out as follows: I began with an intro sheet tab; after this, the next two tabs represent the cleaned data itself (mostly from YouTube but with some self-additions). The first contains all data, while the second contains just a Boolean video category chart. All additional tabs after that contain pivot tables and subsets of the data, each with their own visualizations.

All data came directly from YouTube’s analytics and are expressions of discrete, concrete data; therefore, no bias or credibility issues should exist.

Since I am part owner in the company, I have full rights to the data.

In terms of that discrete, concrete data, what YouTube provides is actually more extensive than the analytics any other hosting platform would share with its users. These include metrics we aren’t entirely concerned with in this analysis, but it also contains many categories very pertinent to the questions we’re trying to answer at large, particularly views, impressions, average percentage viewed, average view duration, and retention rate.

However, despite all the data provided from YouTube, there were a few facets of information not yet represented in the data. So I created a new category for Video Length and another for Intro Length; this was so I’d be able to calculate out in a third column the Intro-to-Video Ratio. After this was complete, almost all four questions would be able to be looked into now except for categories. So, after establishing a multitude of initial categories to mark if a given video contained or not, I marked each video in Boolean fashion according to the content. In a final Boolean column, the deciding factor was if “D&D” was contained in the title or not.

Because of the relatively small size of the data being dealt with in this project, the entirety of the clean up, calculations, visualizations was able to be completed in Google Sheets without the need to import into SQL or R.

Much of the clean up process that did exist within Google Sheets concerned data types: one, applying types of Date and Percentage and the like; and two, specifying decimal amounts and zero-placeholders. 

To better understand the data, first I created a Sum and an Average rows, and I used SUM, AVERAGE, and COUNTIF/COUNTA functions to accomplish that. I then used AVERAGEIFS to calculate average views and average impressions for each video category.

Now, to look toward the questions. **First**, how long are people sticking with each video? Video retention is an excellent measure of this question, because it is a measurement of those still watching at the 30-second mark. We can see below here that, from the beginning of the channel’s history on February 25 until the end of the timeline period, there is a slight but downward trend in overall video retention going down an average of around 5% from its initial peak at around 70%.

![1 1 Video Retention Over History (2_25_23-8_27_23)](https://github.com/i-am-nate/youtube-data/assets/112446964/1a326218-c519-4632-ae48-50c300824d2d)

Yes, this seemed well and good. But why was this happening? So we turned to our **second** question, how does the intro affect retention? Because in the data we have columns for both video duration and intro length, a simple division calculation into a third column gave me a ratio of how much of each video the intro was taking up. So juxtaposing that ratio with our video retention timeline, do we see inverse correlations to perhaps show that the longer an intro takes up of a video the less retention will increase? In fact, we find no correlation one way or the other.

![2 1 Video Retention vs  Intro-to-Video Ratio Over History (2_25_23-8_27_23)](https://github.com/i-am-nate/youtube-data/assets/112446964/660e76e8-f870-4849-9861-63acb93ec04d)

This is confirmed when we compare specifically video retention rate across the various intro-to-video ratios represented: the trend line is almost horizontal, showing no effect one way or the other. This is also true when comparing the intro lengths themselves instead of just the ratios—trending nearly horizontal.

![2 2 Video Retention per Intro-to-Video Ratio](https://github.com/i-am-nate/youtube-data/assets/112446964/1dc65b96-23e7-46ad-9ff2-f10b61f2e551)
![2 3 Video Retention per Intro Length](https://github.com/i-am-nate/youtube-data/assets/112446964/c5d90472-36d6-4f64-9ae0-3fba969dc152)

If intro ratio is non-determinative of higher retention, then **third**, what lies within the data to help us answer how video length affects it? Here we look at 5 factors—views, percentage viewed, view duration, total watch time, and impressions—compared to video length to discover potential correlations. This data would be helpful in determining ideal video length across different categories.

Total views suggested a sweet spot between 9:32-13:58 with pretty sharp drop offs shorter and especially longer than those lengths.

![3 1 Views per Video Length](https://github.com/i-am-nate/youtube-data/assets/112446964/ef607428-e6b9-4504-bfdd-4acba5295677)

Percentage viewed showed that, as the length of the video increased, the percentage of the entire video viewed by those who did indeed watch the video decreases in a decently consistent manner. Although, perhaps intuitively, average view duration ascended upward with near the same slope the percentage viewed graph descended; the average duration rises, even while the average percentage viewed decreases.

![3 2 Percentage Viewed per Video Length](https://github.com/i-am-nate/youtube-data/assets/112446964/b6fa28a1-bb99-489f-99fd-0f613e9d47db)
![3 3 View Duration per Video Length](https://github.com/i-am-nate/youtube-data/assets/112446964/3c14978e-e1ed-4f92-b5ed-a5ba653c5204)

However, when we look at total cumulative watch time per video divided up into length, we find a nearly identical graph and curve as the total views graph: that same sweet spot around 9:32-13:58. We also find the same exact story when comparing impressions instead.

![3 4 Watch Time per Video Length](https://github.com/i-am-nate/youtube-data/assets/112446964/bfaa82a2-86b9-4dd0-b0cb-30f8d8f1e019)
![3 5 Impressions per Video Length](https://github.com/i-am-nate/youtube-data/assets/112446964/09b403f2-3202-46b3-a0c3-a158081276c0)

Finally, **fourth**, are there certain categories that perform better than others? Admittedly, there was an outlier category called ‘Cairn’ that was so off the chart it is not included with the graphs. However, in analyzing each category for the total combined number of views and impressions (impressions divided by 10 for comparison’s sake and with the total number of videos in each category beside each category), it became very obvious that in terms of both views and impressions, ‘D&D’ rose to the top.

![4 1 Views and Impressions per Category](https://github.com/i-am-nate/youtube-data/assets/112446964/8748d487-783f-4fd1-9091-4b5626b4ca50)

To look into this category more and to get a bit more granular, I used AVERAGEIFS functions to check across many different metrics if they would be greater if they contained ‘D&D’ even in the title of the video itself. And across almost every metric, videos with D&D in the title contained a way better chance of leaving impressions and being viewed. An interesting side effect is the slight drop in Average Like Percentage for videos containing D&D, despite its uptick in other categories; this can perhaps be attributed to the topic being more controversial, leading to greater disparity of opinion on video content. Although not accounted for in this dataset, looking at a Comments metric would also be helpful in determining potential controversial videos or topics, as more comments could suggest more dialogue and engagement.

<img width="666" alt="4 2 DnD in title vs not in title" src="https://github.com/i-am-nate/youtube-data/assets/112446964/2d9ee99d-e590-43ba-93e5-8f09600fab76">

Overall, after analyzing the data, we had our results, the answers to the questions being asked of how we could increase channel viewership. We discovered that slowly over the course of the timeline, overall video retention has been slightly decreasing, and the ratio or length of the intro seems irrelevant. Instead, the answers came down to **ideal video length** and **category awareness**. Videos that performed the best had a video length of 9:32-13:58, and videos that contained ‘D&D’ in the title performed better than those that did not have that phrase in the title.
