## Forecast Accuracy Measures

- Forecast accuracy. How do you know how good a forecast is? Well, you have to measure it's accuracy, and you can measure how far away it is from the actual demand, which is defined as accuracy, but you also have to consider bias, and bias means is, do you have a tendency to over forecast or under forecast? You don't want to be too biased in either direction because that degrades the ability to properly forecast the future just as much as accuracy does. The simplest form of a forecast accuracy measure is the mean error. We take our demand, we subtract the forecast from it, and, then, all we need to do is average up all of these time periods that we have forecasted so far, and that gives us our mean error. Both over forecasting and under forecasting are bad.

<img width="1919" height="948" alt="image" src="https://github.com/user-attachments/assets/c7e515fa-11e2-447c-a10e-5dbe13676242" />

- If you over forecast, that means you have more product than you really needed, so you're going to have stuff left over. If you under forecast, you're not going to have enough product, and customers are going to come to your store, not have anything to buy, and they're going to be angry. Next, we have the mean absolute percent error. And unlike the mean error, which was more of a measure of bias, we are going to actually get that accuracy. So we have our demand, minus our forecast. And the problem is that we are trying to compare across products, so we have to divide by demand to get a percentage. And we're going to take the absolute value of that.

<img width="1917" height="946" alt="image" src="https://github.com/user-attachments/assets/5e8438f5-0da5-4904-9763-1610dd0c3b57" />

- So that we don't have pluses and minuses canceling each other out. And then, all we need to do is take this sum of over that and divide by how many periods we have, and then we have it. Make mean absolute percent error. A very important forecasting accuracy measure is the mean squared error or MSE. What we're trying to achieve with that is, that we're trying to give more weight to large errors. Large errors are the ones we want to avoid at all costs because small errors we can plan for. Large errors are going to surprise us and make our life and planning much more difficult.
- So our demand minus our forecast actually will get squared and then we take the average of that. So the MSE is squared errors, and we take the average over all of the forecasted periods. Means Squared Error. Because we're squaring the error terms, what happens when we have a large error, it becomes much larger because we multiply it by itself. Small errors remain small, but large errors become huge! And those huge errors are going to significantly affect our mean squared error, therefore we will be much more sensitive to those large errors. So which forecasting accuracy measure should we look at?

<img width="1919" height="943" alt="image" src="https://github.com/user-attachments/assets/c5a29458-a27e-498f-acb8-7d7d343b4891" />

- The short answer is, all of them. Each one has something different to tell us, and we should consider each one for different reasons. In the end, we want to pick the best forecast. And only if we look at each forecast that we consider, from various measures of accuracy, we'll be able to obtain the best forecast possible.

###########################################################################################################
###########################################################################################################
###########################################################################################################

## Notes on Forecast Accuracy Measures

In this example, I will show you how to implement the following forecast accuracy measures: 

Mean Error

Mean Absolute Percent Error

Mean Squared Error

There are several steps you need to complete:

<img width="1267" height="686" alt="image" src="https://github.com/user-attachments/assets/c5af3b86-a2dc-424b-8ca6-cc022c16b97b" />

<img width="1107" height="703" alt="image" src="https://github.com/user-attachments/assets/8791879e-fb33-407a-96ce-311e9b4f5f29" />

###########################################################################################################
###########################################################################################################
###########################################################################################################

## Forecast Accuracy Measures Screencast

- Forecast Accuracy Screencast. So now, what I would like to show you is how to calculate the three forecast accuracy measures that we discussed in the lecture in a spreadsheet. So, we are going to start with the Mean Error. In order to calculate the Mean Error, you need to calculate the error for each period first, which then you can average together. So, we get the error by taking our demand minus our forecast and there we have it in period three demands 24 forecast is 22 our error is 2. Now as we copy this down, what we see is we have positive and negative errors. We over and underforecast and that's okay.
- That's what we expect from the error. To calculate the mean error, then what we do is we go over here where I've created a spot for it and we take the average of all of these errors that we have, then we have it the mean error in this example is -0.71. Now, let's look at the absolute percent error. So, the absolute percent error needs two parts. One is we need to get an absolute error and then we need to convert it into percent. So, we get the absolute error by taking the absolute value. We already calculated error, so I'll keep using that and then we need to divide it by our demand to get it into a percent form.
- So, the absolute value of the error that we previously calculated divided by demand and then all I need to do is copy this down over here. And now, I go in to this cell that I prepared here from our mean absolute percent error. All I need to do is here. Average all of these values together and here's our result. On average, we have an error of 13.58%. So every time we create a forecast, we're about almost 14% off. We don't know in which direction on average, we're off.
- But in general, this is how far we're off on average. So now, we are looking at the squared error and the squared error simply the squared error value. We raise it to the second power. And all I need to do is drag this formula down, captivated overall of these values and then I have another spot where I see it's the average of all the values in the column G. And here we go. Our Mean Squared Error, MSE is 8.86. Now 8.86 in general, we cannot really make a lot of statements on, but on of the key features of the Mean Squared Error is that larger errors.
- So for example, this forecast error of -7, which is an over forecast of 7, now becomes 49. So in an average, we give it much more than weight than a small error, such as in period 5, 6 and 10, which only has a value of 1 and 1 times 1 stays 1. So what we see here with a Mean Squared Error is an amplification of large errors, which is the ones that we really care about when we forecast. We can deal with small errors, but large errors are the ones that make it much more difficult to perform all of the steps that are required later on. So here, we have the three accuracy measures. The Mean Error, the Mean Absolute Percent Error and the mean Squared Error.

###########################################################################################################
###########################################################################################################
###########################################################################################################

## Moving Average

- Moving average. Let's imagine you're a stock broker on Wall Street in New York City and you're trying to look at a stock. Should you just consider its trading value from yesterday? Well, that seems a little bit shortsided. Or should you look at all of its stock's history? Take, for example Johnson & Johnson. They're over 140 years old.
- What the stock price was 140 years ago probably has not much to do with where it will go in the future. The truth lies somewhere in the middle. You want to look at a moving average that takes a subset of data, averages it, and as we move through time, that average will move with us. So, on the stock market, we often consider 50 and 200 day moving averages as a comparison for the stock price that we currently have. Now, lets take a look at the math behind the moving average. So our forecast, a time T, is equal to a moving average, so we are going to pick a subset of data that we are going to average up, and we denote that again by our Greek symbol sigma, and that sum is going to go from i = t- N + 2 all the way to t- 1. So, t- 1 is the period that we have available right now and we'll going to go back N periods.

<img width="1919" height="950" alt="image" src="https://github.com/user-attachments/assets/d2909aa7-0421-4668-bc7c-76d44bc15584" />

- Now, we have to add the two back in because we really start a t- 1 and we only want to go eight periods back of demand. We divide it by the number of periods that we summed up, which is N, and there we have the formula for the moving average. And if we look at it on a timeline we're here at point t and we are going to, let's say, have an N of four, we are going to average out those four periods, so we're going to sum them, and we're going to divide them by N, which is a moving average. The average, as you saw, is a fairly straight forward mathematical function. But in the moving average, we have one big unknown, and that's called N. N is the number of periods you're going to average together, and that is a decision that you as the forecaster needs to make. A small N will make the forecast very reactive versus a large N, which makes the forecast very stable.
- So you go from something like the method to something like the cumulative mean. Either way, you have to determine what N you pick. And that is not a decision anyone can make for you, unless you know the specific situation in which you will use a forecast. How do you know which N is the right one? Well, it comes down to trial and error. You have to try different values of N, measure accuracy for each one of them, and then pick the best one. So as we've seen the moving average is a tremendously adaptable forecasting method.
- You can make it very reactive, you can make it very stable. And that's why a lot of companies that have reasonably stable demand love to use it.

###########################################################################################################
###########################################################################################################
###########################################################################################################

## Moving Average Notes

In this example, I will show you how to implement the moving average forecast. There are several steps you need to complete:

<img width="1038" height="574" alt="image" src="https://github.com/user-attachments/assets/a98dc28b-a309-4464-af13-af2cee46f98f" />

Notation:
Dt: Demand at the current time period

Ft: Forecast at the current time period

Dt-1: Take the demand from the previous period

N: number of  data points in the moving average

###########################################################################################################
###########################################################################################################
###########################################################################################################

## Screencast on Moving Average

- Moving Average Screencast. Now let's take a look at how to implement the moving average in this spreadsheet. So, the moving average is an average of a set number of periods. Unlike the cumulative mean, where we take all past data into account and average it all up, we're picking a set number of periods that we then average going forward. So in this case, I'm going to use a moving average of 3. And that means we can only start after we have collected 3 periods' worth of demand data. And I'm here in Period 4.
- And now I'm going to start typing in the formula. So type in average, so all we have to do in the spreadsheet is type in the word average, we open the parentheses and then tell the spreadsheet what periods to average together. Now, as you see here, we have an average of the cells B2, B3, and B4. And in this case, I want all of the cells to move as I copy the rows downward. Therefore, I'm not going to add in any dollar signs or anything like that to fix the cells. We also see our result is 22.666666667, and that means that in order to get the same units coming out of the forecast as was goes into the demand, we should apply the round function, Without any decimals. And then it's going to round it up to 23.
- So there is this, and all I need to do now is copy these down. We'll make it appear 31 here. And there you have it. I already included a chart, so we see how it looks graphically. The moving average of 3 is a lot smoother than what we would have with the naive method, but not quite as smooth and stable as the cumulative mean, which becomes a straight line here in the later part of the demand data. So this is the moving average with an N=3. I would like to show you one additional version of this, N=3 should go in here.
- Let's make this a little bigger, and I would like to show you how an N of 5 would look like. It's really not that complicated. All we need to do is wait one, two, three, four, five periods, until we have, Five periods to average together. And then we apply exactly the same formula, average, One, two, three, four, five, together. We want to be consistent with our round function here, no decimals, and there's that. All I need to do is to copy this down. Okay, here is this, and now, I'm going to add in some more data.
- In other words, we are going to add in, Another range, and that will be column D. Okay, here we go. We update our chart. And here's this. So we see the larger N actually makes the forecast a little bit more stable. You can see this a little better here. So it's a little bit more stable then the rather nervous, N=3, so as we increase N, it will actually be a little bit more stable, less like the naive forecast, more like the cumulative mean.
- Now the obvious question becomes now, how do you decide? Do you pick an N of 3 or an N of 5 or something different? Well, that's why we looked at the forecast accuracy metrics. And if I was just to pick one metric that I would trust the most, it would be the mean squared error. So, I'm going to calculate the squared error for my N=3 and the squared error for N=5, taking a small shortcut here, if you don't mind. Let's push this over a little bit, and now, I am taking demand minus forecast. And I'm taking all of that to the second power, and I'm doing the same thing here later on as well, so equals.
- And then, minus our forecast raised to the second power. So now I just copy this. Okay, and then I copy this here. We don't want to use this value. And quite honestly, for calculation purposes, or for comparative purposes, we should use the same number of periods that we averaged in together. So it's going to start here. Let's say MSE (3), and MSE, (5). =average of this stuff here.
- And the MSE (5) is the average of all of these values here. Okay, so it is very close. But we do see that the MSE for the moving average with N=3, or where we average it together three periods, is slightly larger than the moving average where we average five periods together. So if I was going to pick the moving average, either 3 or 5, I would pick the moving average with 5. Because the mean squared error, which is one of the most meaningful accuracy measures, is slightly better. So there you have it. This is the moving average, and I showed you two variations of it.
- One where we average three periods together, and one where we average five periods together.

<img width="931" height="659" alt="image" src="https://github.com/user-attachments/assets/646bdedc-3858-4b7d-ac7d-c4b60a19fef0" />

###########################################################################################################
###########################################################################################################
###########################################################################################################

## About Rounding

You may have noticed that I asked you to round your forecast.  There are several reasons for this:

You plan to "sell" full units, not half units. In other words, your forecast represents the format the of the actual demand.

Your forecast accuracy measure will be misrepresented by decimals. If you forecast in full units, the deviation from the actual will not be the same, thus you introduce randomness that is not really there.

Both these points might seem like pretty small issues, but over a lot of data, this is going to make a difference.

Note of caution: if for whatever reason demand is represented in decimals, then your forecast should be in the same format.

###########################################################################################################
###########################################################################################################
###########################################################################################################

