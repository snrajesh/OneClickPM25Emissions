## Introduction

This application provides a comparative overview of fine particle (PM25) emissions  in the United States.
In a nutshell, this application provides a comparative overview of fine particle (PM2.5) emissions in the United States.

This application was developed as part of the Data Science course on Developing Data Products (from JOhns Hopkins University via Coursera). The application is built using R, Rstudio, and Shinny.


## Scope
Fine particulate matter (PM2.5) is an ambient air pollutant for which there is strong evidence that it is harmful to human health. In the United States, the Environmental Protection Agency (EPA) is tasked with setting national ambient air quality standards for fine PM and for tracking the emissions of this pollutant into the atmosphere. Approximatly every 3 years, the EPA releases its database on emissions of PM2.5. This database is known as the National Emissions Inventory (NEI). 

For each year and for each type of PM source, the NEI records how many tons of PM2.5 were emitted from that source over the course of the entire year. The data that we will use for this application are for 1999, 2002, 2005, and 2008.
  
  
#### Who is this for?

***If you are:*** 
* Looking to move to a new town with better air quality?  
* Or concerned about the air quality of your current town?  
* But don't know how to get the information?  
  
***The App can help...***   
 
In a nutshell, this application provides a comparative overview of fine particle (PM2.5) emissions in the United States.

- **Walk-Up-And-Use** type App (i.e. no training needed)  
- A **Color-Coded USA map** with shades based on emissions
- With **One Click** you can drill down to a state and see all info
- Plots showing **emission trend** for your state of choice
- Easy access to **Supporting data** for curious users
   
  
## Instructions

#### How to use?

This is a "Walk-Up-And-Use" kind of application, so no training is needed to use this application.  
  
1. On the Left-Panel, you will see a **drop-down list** of state-codes.  
2. Select the **state-code** by scrolling the list (***That is all you need to do!!!***).  
3. As soon as you select the state-code, the application will analyze the data for your state.  
4. You will see the state map below the drop-down list and the charts on the main-panel are refreshed with the data for your state.  

#### What am I looking at?

OK, now you see some fancy pictures...

1. The state map shows each county color-shaded based on emissions: 
    + counties in the darkest blue are the ones with highest emissions (in 76-100 percentile)
    + counties in the lightest blue are the ones with lowest emissions (in 0-25 percentile)
    + the rest are in 25-75 percentile
2. The first plot on the Main-Panel shows the **Trend of Emissions** for the selected state over the last 10 years. As well as a projected line (in green) showing the trend, derived using linear regression model. The details of the linear regression model is all the way at the bottom of the page.
3. The second chart shows the **Emissions in the counties** within the state. It is color-coded to show the different emission sources.
4. Click on **Emissions Data** tab to see latest emissions data at the county level for the state you selected.  
5. Click on **All Data** tab if you are curious to see all emissions data for all sources in all counties of all states in the US. This is an interactive table; so you can filter it to your state or county.  
6. Don't be afraid to click on the additional tabs to see additional information...  
    
### Under the hood
  
How did we do this?

* This app is built using R tools ***(R is a programming language and software environment for statistical computing and graphics supported by the R Foundation for Statistical Computing)***.  
* We used R, Rstudio, and Rstudio's Shinny to build the application and the App is hosted on Rstudio's Shinny servers.  
* The source of the data is the EPA National Emissions Inventory web site  (http://www.epa.gov/ttn/chief/eiinformation.html).
  
...
