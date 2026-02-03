## What is Supply Chain Planning?

- Imagine you're a pastry chef at the local bakery. How many croissants are you going to make for tomorrow? Or you own a gas station, how many trucks are going to stop here to fill up? Supply chain planning answers all of these questions. It's the foundation of all other supply chain tasks. Sourcing, operations and logistics, all of which depend on the accurate prediction of demand. I'm Rudi Leuschner with Rutgers Business School and I'm excited to teach you about planning.
- [NOISE] [MUSIC] Precision planning. Precision planning [SOUND] every company from your local buttery bakery to the multinational all in gas corporation Exxon Mobile must be able to match supply with demand. Without planning all other links in the supply chain will be broken in any marketplace. If you're considering a career in supply chain management, are already in the field or simply fascinated by how to forecast demand, this course is for you. [MUSIC] You.

###########################################################################################################
###########################################################################################################
###########################################################################################################

## Is this course for me?

Dear learner,
thank you for taking the time to look at this  course. Please take a look at the following to understand what you are  going to be able to do after completing this course, who this course was  designed for and to ensure you are getting the most out of this course.

Why Supply Chain Planning?
Any well-functioning supply chain is based on planning.  In this course, you will master some of the most essential forecasting methods commonly used in practice. Without proper planning any supply chain will fail to match supply with demand. 

An Introduction to Planning
In  this introductory Supply Chain Planning course, I will take you on a journey to this fascinating aspect of the supply chain, which is to predict, project, and estimate future demand. Please note that the idea for this course is  to introduce learners to the art and science of forecasting. While I am planning to cover the  most important pieces, this is not meant to be exhaustive nor should you  expect to be an expert upon completion. But my goal is to show the  major pieces of planning in a fun manner and hopefully this will  encourage you to learn more.

What topics will you cover?
We cover the four major forecasting methods and three measures of forecast accuracy:

Naive Forecast

Cumulative Mean

Moving Average

Exponential Smoothing

Mean Error

Mean Absolute Percent Error

Mean Squared Error

What will I be able to do upon completing this course?
You will master different forecasting methods.

You will be able to differentiate the advantages  and disadvantages of different forecasting methods by applying and weighing different accuracy measures.

You will be able to make purchasing, manufacturing, and logistics decisions based on a forecast you created.

Who is this course for?
This  introductory course is designed for three general audiences. While this  is not an exhaustive list, you should be able to see yourself in one of  these three groups: 

Those of you who are exploring a career  in Supply Chain Management, but lack the any background. This course  will provide you with a general overview of the field of Supply Chain Planning.

Those of you who are working with people in Supply Chain Planing and want to understand their daily challenges better. 

Those  of you who are fascinated by how to predict, project and estimate future demand.

What do I need to start?
This  is an introductory course designed to provide you  with a start on your learning journey in operations. As such,  you do not need to  have any background in Supply Chain Planning, but it would be beneficial if you had a  basic understanding of: 

General business concepts

Basics of spreadsheets

Basics of statistics

###########################################################################################################
###########################################################################################################
###########################################################################################################

## So, you want to forecast demand?

- So, you want to forecast demand. Imagine you're opening your own business, a bakery and you're making the best croissants in town. It's the first day and you're just getting started. How many croissants do you need to make? It's a hard question, because you don't have any history, you don't know how many customers are going to show up. Nevertheless, a system of forecasting is necessary for any business. You need to figure out what customers are going to buy and forecasting is the way to get there.
- Imagine that it's a year later and you are still in business making croissants, does it get any easier? You have some history to go on, but you still don't know what customers are going to do. Forecasting is an essential part of every business. Let's define forecasting. It's the prediction, we're going to guess what demand will do. Estimation, we're going to guess what level it will be at. And projection, carrying it into the future of demand.

<img width="1919" height="914" alt="image" src="https://github.com/user-attachments/assets/e22f7ea1-e5e5-4d89-a434-296159a97b5c" />

- There are several types of forecasting approaches, what we're going to use here is time series and time series relies on historical data. We have demand recorded over time from past until the future and we're sitting here at point t, and this demand data is going to be recorded in equal size intervals of time. So that maybe a day, it maybe week, it maybe a month or even a year. So, we have this equal size periods of time and we are going to forecast in those same intervals into the future. Our goal is to build forecasting model based on past demand, which we denote as d typically and we are going to forecast into the future and we denote that as F. Once future data comes in, we're going to continuously refine our forecasting approach and hopefully have a forecasting method that minimizes the error and gets us the best prediction possible. Time series are mad up of several different patterns and noise, which I'll discuss in a second.
- The different types of patterns that we typically see in time series are a base level of demand gives us a starting value, any trend that might persist. So, either demand goes up over time or it goes down over time. Seasonality. Seasonality is a pattern that repeats every month, every quarter or every year. Longer range cycles, everything that's longer than a year, we call a cycle. It works like seasonality. And finally, we have noise
- Noise is random. It follows no rhyme or reason, but it's always there. A good forecast will try to resolve all of the pattern without trying to forecast noise. We cannot forecast randomness, so the best forecast does not even try. Before we get started with our different forecasting methods, a few words of caution. The best forecast is not always the most complicated one. In fact, if you can have an equally good forecast that is more simple, it's a better one to use.
- Now when it comes to forecasting, it's equally art and science. We have scientific methods available, but using it right and picking the right one is equally important and it takes a lot of work to continuously monitor how different methods are doing and picking the right one at the right time. A lot of people will tell you maybe that forecasting is always wrong, because you don't always hit the number exactly that you predict. But remember this, if you just get a little bit closer than before, you have an advantage. And if the forecast is right or better, then everything else in the whole supply chain will work so much better. Therefore, forecasting is one of the critical pieces of supply chain management.

###########################################################################################################
###########################################################################################################
###########################################################################################################

## The Naive Forecast

- The naive forecast. Let's start with the most simple form of forecast. It is called the naive method. It's naive because all we're doing is, we're saying what we sold yesterday, that's how much we're going to sell today. What we sell today is the number we're going to project for tomorrow. It doesn't take a lot. And it's very simple and easy to use.
- If we sold 20 croissants yesterday, we're going to sell 20 croissants today. If we sell 20 croissants today, we're going to sell 20 croissants tomorrow. The naive forecast works very well in certain situations. And it sometimes works even better than other more complicated methods. The naive method can be represented mathematically as well. So our forecast, we denote that again as F. And we're going to forecast into the current time period, so it would be F sub t.

<img width="1919" height="941" alt="image" src="https://github.com/user-attachments/assets/145dd686-c907-49d2-9dc4-60fb8620d1cb" />

- And we set that equal to our demand at t- 1. And that means the previous time interval. If we look at it on a timeframe then we are trying to forecast here and we are going to use this level of data demand. At minus 1 as our forecast at period t. We can make several adaptations to the naive method. For example, if we have our forecast, and rather than using the previous time period as our demand, we have a forecast that is very seasonal. So it's more applicable to use the same month last year then we would do something like this.

<img width="1919" height="936" alt="image" src="https://github.com/user-attachments/assets/184befdf-118c-44be-9e7e-66e6b19a7413" />

- So we're recording time in equal size monthly buckets, and we're going to say t-12 because that is the same month 12 years back or one year back. And that would be an example of a seasonal naive method. Another version of this would be if we use Our demand at the previous time period, but we do know that we are growing every month, and we know for example every month we sell T units more, and therefore we add that T into our forecast. The naive method is clearly simple, but in situations where other more complex forecasts are not doing very well, it may be equally good and remember what we said earlier. If you can use a simpler method and get the same level of accuracy, it's better than using a more complex one. Now the naive forecast is very noisy because it doesn't filter out any noise whatsoever. That makes it very nervous but also responsive to changes in demand.
- Nervous means we have a very volatile forecast. That may not be in our best interest when we're trying to plan for a smooth production. Therefore, we have to understand that typically, only the last period is used for our forecast. That is a big assumption, and it may not be very realistic. However, the naive method can be used as a benchmark to more complex methods and it tells you whether a more complex method is clearly superior.

###########################################################################################################
###########################################################################################################
###########################################################################################################

## Naive Forecast Example

In this example, I will show you how to implement the naive forecast. There are several steps you need to complete:

<img width="1153" height="530" alt="image" src="https://github.com/user-attachments/assets/1a995b74-01c7-4da4-bfef-51bad222b6c4" />

###########################################################################################################
###########################################################################################################
###########################################################################################################

## Naive Forecast Screencast

- Naive Forecast Screencast. In this screencast I will show you how to implement the naive method onto a spreadsheet. And for most people that are forecasting demand, they will forecast using a spreadsheet whether it is Google Sheets, like this, Excel, or anything similar. The idea is that we can quickly implement formula onto the spreadsheet, and then we can do it over and over with very, very little additional work. What I have here is, 30 periods worth of demand that are here in column B, as you see this here. And the task will be to implement the Naive Forecast into column C by applying the Naive Forecast formula, and then we're just going to copy it down. The Naive Forecast, just it was a refresher, we're using the most recent period of demand to predict the next period.
- In this case, what we are saying we cannot start the forecast until the second period. We will have had some kind of history to go on. And I am going to say, since we just observed period one's demand we're going got set period two's forecast equal to the demand of period one. And then I hit Enter, and here is my forecast. In period one we had demand of 20. That will be my forecast for period two. And then, to use it for the other periods it's fairly simple because I just need to copy down this formula, and voilà.
- Now here we have the forecast. And as you see, it is exactly the same value as one period earlier. There's not much to this. To visualize this, I would like to just graph this. We insert a chart. And we would like it to be a line chart. And that looks pretty good.
- We have our periods here, our demand, and here is our chart. I'll move this over a little bit. Pretty good. Now what you see here is, the line is basically shifted one period to the right or one period later in time. One thing that bothers me though is I like my. Axis to go from zero all the way to a little bit over. It looks better and it gives you much more of a sense on the volatility.

<img width="1912" height="940" alt="image" src="https://github.com/user-attachments/assets/06694fb6-d2e0-43a6-809f-a2c1d58c74d4" />

- There you have it. Here is the Naive Forecast implemented into a spreadsheet. And we apply the formula, we copied it down, we charted it and this is what you get as a result.

###########################################################################################################
###########################################################################################################
###########################################################################################################

## The Cumulative Mean

- The cumulative mean. In the naive method, we assumed that only the last piece of information is useful in predicting the future, but what if we think that all prior data is useful in our forecast? That is the idea behind the cumulative mean. We take all of the data that we have, average it, and that is going to represent our forecast. Now let's look at the math. The cumulative mean is, again, denoted by F sub t, which is what we're trying to forecast. And that is made up of the sum of demand, and that sum is going from the very first period we have, I=1, all the way to T-1, which is the very latest time period we have available.
- And we are going to divide that by how many periods we had summed together and that would be t-1, and that gives us an average over all periods. So what this means on time frame is, if we are right here at t, then we are going to average all the demand from the prior periods and make that our forecast right here, a time t. So, how good is the cumulative mean? Well, it may work well in some situations and it's really the antithesis to the naive method. Where's the naive method? Was it very responsive, but also picked up a lot of noise? This forecast is very stable and averages out all the noise, so it really filters it out.

<img width="1918" height="920" alt="image" src="https://github.com/user-attachments/assets/f8b7c531-3cb3-425a-85da-d2e37901ca17" />

- If you have a situation where your overall demand is built only by the level and noise, no other patterns, then this is a good forecast to use. And advantage is, as I said, it's stable. But it also may not recognize all the pattern, and you need to be careful how to use it. The big assumption in the cumulative mean is that all prior data is equally useful. That may not be very robust, but it is the assumption. And there are other methods that may take into account that flaw in the cumulative mean.

###########################################################################################################
###########################################################################################################
###########################################################################################################

## Cumulative Mean Example

In this example, I will show you how to implement the cumulative mean forecast. There are several steps you need to complete:

<img width="1091" height="555" alt="image" src="https://github.com/user-attachments/assets/e92ecc18-b433-4958-8163-834b92b0f578" />

###########################################################################################################
###########################################################################################################
###########################################################################################################

## Cumulative Mean Screencast

- Cumulative Mean Screencast. The cumulative mean is a forecast method that is taking an average of all prior demand. So as we discussed in the lecture, as we go through time, and there are more and more periods available, our average rows over more and more data points. In order to implement it, it's actually quite simple. There's only a few little things that we need to be careful about. So the first period in which we can implement accumulative mean is really period three, because before then, we don't really have anything to average together. And in that period, we have two terms that we average together.
- As we go through the time, we will have more and more periods to average together. So, In order to get an average, we type in the word average, open the parenthesis, and then select the two cells that we want to average together. Now, if I were to just hit enter at this point, what will happen later as I try to copy that formula across the multiple rows is that those two prior periods of demand are all that I'm going to average. But that's not what I want. I want it to always start at this cell, B2, and then go up until the last period of demand that we have just observed. So in order to achieve that, I have to put in a dollar sign in between the B and the 2. You can also put 1 in front of the B for good measure if you wanted to, but that's optional, it works either way.
- So once I hit enter, we have our average. You'll see the dollar signs in here, and now I can copy this formula down and copy it all the way here, and here is our cumulative mean. So now, one thing jumps out at you right away, I hope. We see a lot of decimals because the average is not always going to be an integer, so that is something that we need to take care of. And one recommendation I have is whenever you have a forecast, try to forecast in the same way that demand comes in. So in this case, it's integer values. There's no halves, or quarters, or any decimals.
- So we want to make sure your forecast comes out exactly the same way. And there's this round function, which basically converts our result into a rounded output where you don't want any decimal points. So there's that, and if I copy this formula down, here is our result, and there you go. Now, some of you at this point may wonder, why don't you just remove the decimals with this part here? Well, you could do that. And here we see there are no decimals. So I could remove them that way.
- However, in my calculations later on, they will still be there. And as we calculate accuracy, for example, it's still going to impact it. So it is better to have a clean forecast just the way you would use it rather than have all those decimal points hidden in there. So here we have a chart of our demand versus our accumulative mean forecast. And what see here is that over time, our forecast becomes basically like a flat line because we have more and more periods that we can average together. And that each new period provides very little weight on the overall average. So that's basically one of the things that you get with accumulative mean.

<img width="1919" height="941" alt="image" src="https://github.com/user-attachments/assets/919483b6-ba45-4671-bbe8-2c592cd4a810" />

###########################################################################################################
###########################################################################################################
###########################################################################################################

