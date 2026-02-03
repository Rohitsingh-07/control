## Exponential Smoothing

- Exponential smoothing, take for example ARM & HAMMER baking soda. It's a product you can use for baking, cleaning, or even brushing your teeth. Therefore, we expect demand to be fairly stable over time. We don't expect people all of a sudden to use much more or much less. This makes it a great candidate for exponential smoothing. Exponential smoothing, similarly to the moving average, is a very versatile method. But actually, I like it even better because it is much more elegant to implement.
- By changing one value, you can make it more reactive or more stable. Now let's take a look behind the math of the exponential smoothing formula. So our forecast again is denoted by F sub t. And that is equal to alpha, and I'll explain what alpha means, times, Our demand at t sub 1 + (1- alpha) times our previous forecast at t- 1. So, what we're doing here is we are balancing how much weight we give to our previous or most recent demand and how much weight we're giving to all of the forecasts. And through this part everything is being linked back all the way to the first information available. And this alpha and the 1- alpha are setting the weights of our weighted moving average.

<img width="1911" height="807" alt="image" src="https://github.com/user-attachments/assets/d602c53b-3ba3-4c34-9cd7-404fa53cee0f" />

- So there you have exponential smoothing. So how do you know what value of alpha to pick? For moving average we said you have to do trial and error. And this is slightly true for exponential smoothing as well. However, rather than redoing the forecast over and over, all we need to do is change the value of alpha from larger to smaller. And it makes the forecast either more reactive or more stable. Now, when you change these different values for alpha, you have to keep looking at your accuracy.
- If your accuracy is improving, then you're going in the right direction. If your accuracy's getting worse, you're going in the wrong direction. Luckily, because we have two cells in a spreadsheet that we need to monitor and adjust, it's something that we can automate. And I will show you this later. There are a number of extensions to the exponential smoothing formula. You can use the basic principle to not just forecast stable demand, as we've done so far. But you can take into account trended data, which means you have a consistent increase over time or decrease over time.
- Or you can estimate demand that is seasonal. That is, we have a consistent pattern, or demand data that is both trended and seasonal. So the options are limitless by using just this basic exponential smoothing formula, making some adaptations to it, and using it for a completely new purpose. 

###########################################################################################################
###########################################################################################################
###########################################################################################################

## Exponential Smoothing Notes

- In this example, I will show you how to implement the exponential smoothing forecast. There are several steps you need to complete:

<img width="894" height="654" alt="image" src="https://github.com/user-attachments/assets/ffe466ac-e263-46dc-8be4-04e27efdfca9" />

###########################################################################################################
###########################################################################################################
###########################################################################################################

## Exponential Smothing Screencast

- Exponential smoothing screen cast. Now let's look at the exponential smoothing forecasting method. Which is a forecasting method that takes an average view of all past demand, but it weights more recent data more heavily, and older data less heavily. So we get something that resembles more the moving average, than the cumulative mean, even though it takes into account all demand data. So, now let's take a look at how we were going to implement it into a spreadsheet. In order to start the exponential smoothing formula we have to have an initialization value. Because the forecast itself depends on past demand and past forecast.
- So to start we are going to take a naive view of demand and we're going to use the value of 20 as our initialization value. Then in period 2 we can apply the exponential smoothing formula. Now, let's take care of the round function ahead of time. In order to set up the exponential smoothing formula, we have this coefficient called alpha which we can actually vary. And to do that more efficiently, I'm going to use a separate cell for alpha because then that allows me to just change one cell and vary how reactive or how smooth the forecast is. So alpha has to be a fixed cell, Which means we need a dollar sign right in here, Times, Past demand, Plus 1 minus alpha and that needs a dollar sign, times the prior forecast. So the exponential smoothing formula is made up of alpha times prior demand plus 1 minus alpha times the prior forecast.
- And that way it takes into account with a certain weighting of prior forecast, and how well they did. So now all I need to do is, tell the round function that we don't want any decimals, and here is our forecast exponential smoothing. And we're not going to see much until we have a value of alpha, but let me just write this down first, okay. Now this defaults to, The 0 here. So that means, with an alpha of 0, we place no weight on prior demand all the way to the prior forecast, so that's why you see all of these values as 20. So alpha we can set as anything between 0 and 1. So let's set for example to point 1, And we don't see much happening.
- Point 3, here we see some stuff happening already. Now the question becomes, what value of alpha should you pick? And we can do it graphically because we see, well, 0.4 becomes a little bit more reactive, 0.5 even more so. But how reactive is too reactive, and what really makes for a good forecast? So, in order to decide, we have to calculate an accuracy statistic. I like that mean squared error the best, so here we start it. Demand minus forecast, you'll want to square that.
- There we go. I'm going to copy that down. There's that, now I'm not using the very first period because this was just an estimate, and it has nothing to do with exponential smoothing. So on period 31, we also don't have any demand data, so I didn't calculate a squared error for that. But we have anything from period 2 all the way through period 30. So the mean squared error becomes, the average of all those error values. Okay, up until here.
- And it's about 10.75. When we look at this forecast, if we let's say increase alpha, okay, well increasing it from 0.5 to 0.6 gave us an increase in MSE, so it made it less accurate, that's no good. What if we make it smaller? Well, that made it a little better. What if we go even smaller? Okay, it gets even better. So we could play this game over and over, until we find a value that is optimal.

<img width="963" height="673" alt="image" src="https://github.com/user-attachments/assets/f0745756-7e14-48f1-a622-9fbc2b0d9425" />

###########################################################################################################
###########################################################################################################
###########################################################################################################

## Optimizing Exponential Smoothing

- The simplicity of the Exponential Smoothing formula enables you to automate the optimization of the smoothing coefficient (which we call alpha). This is done with a tool called Solver, which requires a little bit of knowledge, but can substantially enhance your ability to make your forecast better. While you can access this via Google Sheets, I found Excel much easier.  Take a look at this video I created a long time ago that shows how it can be done:
- Forecasting with Exponential Smoothing in Excel - https://www.youtube.com/watch?v=6P-qGU8EYmI

###########################################################################################################
###########################################################################################################
###########################################################################################################

## Selecting the Best Forecast

- Selecting the best forecast. We talked about the knife method, the cumulative mean, the moving average, and the exponential smoothing. As a forecaster, how do I know what to pick? Well, you have to look at it's accuracy and other things. But the first step you should take is look at the graph. If you look at the forecast visually and see how it matches up against actual demand, there's a lot you can learn, so that should be your first step. Then in the second step, take a look at the data.
- Take some measurements. Look at the mean. Look at the minimum. Look at the maximum. Calculate the standard deviation. Calculate the coefficient of variation. That will tell you, how much uncertainly there is in your demand data.
- And then look at your forecast, how much variance does it explain? Now in general, when we are selecting a forecast, we're looking at a couple of things. We want to look at the graph, make sure it's visually closed. We want to make sure it's unbiased, we don't tend to over or under forecast. We want to be close. And most importantly, we want to avoid huge errors in our forecast. So those four things are the critical issues when selecting a forecast.
- So now that we've identified the best forecasting method, all we need to do is hit go and sit back, right? Well not quite. Just because your forecast was the best method on past data, it doesn't mean it's going to work in the future. You can't just sit back and relax now. You have to constantly monitor your forecast, and make sure that what you picked in the past is still the best method out there. It may change over time, and you have to be ready to switch methods at any moment's notice. So your job is never done forecasting.

###########################################################################################################
###########################################################################################################
###########################################################################################################

## Forecasting Best Practices

This is an excellent guide for forecasters going over a number of forecasting practices:

Standards and Practices for Forecasting, by J. Scott Armstrong, The Wharton School, University of Pennsylvania - https://repository.upenn.edu/entities/publication/71ff223f-a28c-4f02-b3b8-f0e01c8b29ca

###########################################################################################################
###########################################################################################################
###########################################################################################################

