Download Link: https://assignmentchef.com/product/solved-fe621-homework-1
<br>
For all the problems in this assignment you need to design and use a computer program, output results and present the results in nicely formatted tables and figures. The computer program may be written in any programming language you want. Please write comments to all the parts of your code. They are a requirement and they will be graded.

You need to submit a PDF containing the report. Please use a word processor such as Microsoft Word, L<sup>A</sup>TEX, or whatever Apple uses to create your report. You will be judged by the quality of the writing and the interpretation of the results.

<em>Part 1. </em>(20 points) Data gathering component

<ol>

 <li>Write a function (program) to connect to sources and download data from one of the following sources:

  <ul>

   <li>GOOGLE finance <a href="https://www.google.com/finance">http://www.google.com/finance</a></li>

   <li>Yahoo Finance <a href="https://finance.yahoo.com/">http://finance.yahoo.com</a></li>

   <li>Bloomberg</li>

  </ul></li>

</ol>

<strong>Notes. </strong>For extra credit you can turn in code to download data from the other two sources. Please note that the program needs to download both option data and equity data. For this problem (and only for this problem) you may use any built in function or toolbox that will facilitate your work. The data will have to be clean (no duplicated values, only one exchange, every column labeled properly, in other words, consolidated).

<strong>Note on Bloomberg data. </strong>For the Bloomberg source, access to one of Bloomberg terminals in the lab is required. If you use Bloomberg data, you may use the API to download data in Excel automatically and organize the data. However, this should be accomplished with an automatic script. If you use R to interface with the Bloomberg data, a useful package for that is Rblpapi, but there are other packages. For the online students, who do not have access to Bloomberg terminals, you may read about the package quantmod in R to download yahoo and google data automatically.

Bonus (5 points) Create a program that is capable of downloading multiple assets, combine them with the associated time column, and save the data into a csv or excel file.

<ol start="2">

 <li>With the function created in problem 1, download data on both options and equity for the following symbols:

  <ul>

   <li>AMZN</li>

   <li>SPY</li>

   <li>VIX</li>

  </ul></li>

</ol>

for two consecutive days (does not matter when) during the trading day (9:30am to 4:00pm). Please record the asset values (both AMZN and SPY) at the time when downloading is done. Please do the same with the VIX. Please note that the traditionally options used to mature the third Friday on the month, however we now have weekly options expiring Friday of every week. You should download all the option chains until the ones maturing two to three months from the date you are downloading. Please discard the options maturing the week you are downloading as their volatility values are way different than those in other weeks.

We shall refer to the data sets gathered in the two consecutive days as DATA1 (for the first day) and DATA2 (for the second day) respectively throughout this assignment and the following ones.

<ol start="3">

 <li>Write a paragraph describing the symbols you are downloading data for. Explain what is the SPY and its purpose. (Hint: look up the definition of an ETF). Explain what is VIX and its purpose. Understand how the options’ symbol is created. Can you determine the option’s expiration from the ticker? Write this information and turn it in.</li>

 <li>The following items will also need to be recorded:

  <ul>

   <li>The underlying equity or ETF price at the exact moment when the rest of the data is downloaded.</li>

   <li>The short-term interest rate which may be obtained here:</li>

  </ul></li>

</ol>

<a href="https://www.federalreserve.gov/releases/H15/Current/">http://www.federalreserve.gov/releases/H15/Current/</a><a href="https://www.federalreserve.gov/releases/H15/Current/">.</a> There are a lot of rates posted on the site – they are all yearly, <em>they are in percents and need to be converted to numbers. </em>There is no theoretical recommendation on which to use, I used to use 3-months Treasury bills which are not available anymore. Since then I have been using the “Federal funds (effective)” rate but you can go ahead and try others. You should remember to be consistent in your choice. Also, make sure that the interest rate that you use is for the same day when the data you use for the implied volatility was gathered and note that the data is typically quoted in percents (you will need numbers). The same site has a link to past

(historical) interest rates.

<ul>

 <li>Time to Maturity.</li>

</ul>

<strong>Part 2.</strong>Analysis of the data.

<ol start="5">

 <li>Using your choice of computer programming language implement the Black-Scholes formulas as a function of current stock price <em>S</em><sub>0</sub>, volatility <em>σ</em>, time to expiration <em>T </em>− <em>t </em>(in years), strike price <em>K </em>and short-term interest rate <em>r </em>(annual). Please note that no toolbox function is allowed but you may use the normal cumulative distribution function (CDF) calculation.</li>

 <li>Implement the Bisection method to find the root of arbitrary functions. Apply this method to calculate the implied volatility on the first day you downloaded (DATA1). For this purpose use as the option value the average of bid and ask price if they both exist (and if their corresponding volume is nonzero). Also use a tolerance level of 10<sup>−6</sup>. Report the implied volatility at the money (for the option with strike price closest to the traded stock price). You need to do it for both the stock and the ETF data you have (you do not need to do this for VIX). Then average all the implied volatilities for the options between in-the-money and out-of-the-money.</li>

</ol>

<strong>Note. </strong>There is no clearly defined boundary between options at-themoney and out-of-the-money or in-the-money options. If we define moneyness as the ratio between <em>S</em><sub>0 </sub>the stock price today and <em>K </em>the strike price of the option some people use values of moneyness between 0.95 and 1.05 to define the options at the money. Yet, other authors use between 0.9 and 1.1. Use these guidelines if you wish to determine which options’ implied volatilities should be averaged.

<ol start="7">

 <li>Implement the Newton method/Secant method or Muller method to find the root of arbitrary functions. You will need to discover the formula for the option’s derivative with respect to the volatility <em>σ</em>. Apply these methods to the same options as in the previous problem. Compare the time it takes to get the root with the same level of accuracy.</li>

 <li>Present a table reporting the implied volatility values obtained for every maturity, option type and stock. Also compile the average volatilities as described in the previous point. Comment on the observed difference in values obtained for AMZN and SPY. Compare with the current value of the VIX. Comment on what happens when the maturity increases. Comment on what happen when the options become in the money respectively out of the money.</li>

 <li>For each option in your table calculate the price of the different type (Call/Put) using the Put-Call parity (please see Section 4 from [<strong>?</strong>]). Compare the resulting values with the BID/ASK values for the corresponding option if they exist.</li>

 <li>Consider the implied volatility values obtained in the previous parts. Create a 2 dimensional plot of implied volatilities versus strike <em>K </em>for the closest to maturity options. What do you observe? Plot all implied volatilities for the three different maturities on the same plot, where you use a different color for each maturity. In total there should be 3 sets of points plotted with different color. (BONUS) Create a 3D plot of the same implied vols as a function of both maturity and strike, i.e.: <em>σ</em>(<em>τ<sub>i</sub>,K<sub>j</sub></em>) where <em>i </em>= 1<em>,</em>2<em>,</em>3, and <em>j </em>= 1<em>,</em>2<em>,…,</em></li>

 <li>(Greeks) Calculate the derivatives of the call option price with respect to <em>S </em>(Delta), and <em>σ </em>(Vega) and the second derivative with respect to <em>S </em>(Gamma). First use the Black Scholes formula then approximate these derivatives using an approximation of the partial derivatives. Compare the numbers obtained by the two methods. Output a table containing all derivatives thus calculated.</li>

 <li>Next we will use the second dataset DATA2. For each strike price in the data use the Stock price for the same day, the implied volatility you calculated from DATA1 and the current short-term interest rate (corresponding to the day on which DATA2 was gathered). Use the Black-Scholes formula, to calculate the option price.</li>

</ol>

<strong>Part 3.</strong> Numerical Integration of real-valued functions.

Consider the real–valued function

<em>, </em>for <em>x </em>6= 0<em>, </em>for <em>x </em>= 0<em>.</em>

Note that we can actually calculate this integral as: .

<ol>

 <li>Implement the trapezoidal and the Simpson’s quadrature rules to numerically approximate the indefinite integral above. <em>Hint: </em>you can approximate the indefinite integral by considering a large interval [−<em>a,</em>+<em>a</em>]</li>

</ol>

(for example <em>a </em>= 10<sup>6</sup>). Consider equidistant nodes<em>, </em>i.e., <em>x<sub>n </sub></em>= , where <em>N </em>is a large integer.

<ol start="2">

 <li>Compute the truncation error for the numerical algorithms implemented in 1 for a particular <em>a </em>∈ R and <em>N </em>∈ N. That is, create a function of <em>a </em>and <em>N </em>that will output <em>I<sub>N </sub></em>− <em>π</em>, where <em>I<sub>N,a </sub></em>is the numerical approximation of the integral. Study the changes in the approximation as <em>N </em>and <em>a </em>increase as well as the difference between the two quadrature approximations. Please write your observations.</li>

 <li>In a typical scenario we do not know the true value of the integral. Thus, to ensure the convergence of the numerical algorithms we pick a small tolerance value <em>ε </em>and we check at every iteration <em>k </em>= 1<em>,</em>2<em>,… </em>if the following condition holds:</li>

</ol>

|<em>I<sub>k </sub></em>− <em>I<sub>k</sub></em><sub>−1</sub>| <em>&lt; ε,</em>

where <em>I<sub>k </sub></em>is the value of the integral at step <em>k</em>. When the condition holds, the algorithm stops. Evaluate the number of steps until the algorithms from a) reach convergence for <em>ε </em>= 10<sup>−4</sup>. What do you observe?

<ol start="4">

 <li>Consider</li>

</ol>

<em>g</em>(<em>x</em>) = 1 + <em>e</em><sup>−<em>x</em></sup><sup>2 </sup>sin(8<em>x</em><sup>2<em>/</em>3</sup>)<em>.</em>

Use the trapezoidal rule and Simpson’s rule to approximate.

Use a tolerance level of <em>ε </em>= 10<sup>−4</sup>.