---
title: "Developing Data Products : Course Project"
author: "Rajesh Nambiar"
date: "November 21, 2015"
output: html_document
---


## Introduction

This project is part of the Data Science course on Developing Data Products (from JOhns Hopkins University via Coursera). The application is built using R, Rstudio, and Shinny. The web application is hosted on Rstudio's Shinyapps.io. A pitch presentation is developed using Rstudio Presenter and published on Rpubs.

This application provides a comparative overview of fine particle (PM25) emissions  in the United States.
In a nutshell, this application provides a comparative overview of fine particle (PM2.5) emissions in the United States.
  
## Data
Fine particulate matter (PM2.5) is an ambient air pollutant for which there is strong evidence that it is harmful to human health. In the United States, the Environmental Protection Agency (EPA) is tasked with setting national ambient air quality standards for fine PM and for tracking the emissions of this pollutant into the atmosphere. Approximatly every 3 years, the EPA releases its database on emissions of PM2.5. This database is known as the National Emissions Inventory (NEI). 

For each year and for each type of PM source, the NEI records how many tons of PM2.5 were emitted from that source over the course of the entire year. The data that we will use for this application are for 1999, 2002, 2005, and 2008.
  
  
## Data Processing

#### A. Pre-processing:
1. The emissions data is downloaded from [NEI Website]('https://d396qusza40orc.cloudfront.net/exdata%2Fdata%2FNEI_data.zip'), and loaded the file summarySCC_PM25.rds into a data frame, `pm25emissions`, using `readRDS`.
2. The county fips data is downloaded from [Census Website]('http://www2.census.gov/geo/docs/reference/codes/files/national_county.txt'), and loaded into `fips` data frame, using `readRDS`.
3. A `states` data frame is created by merging state.abb,state.name, and state.x77 data in R to have state-code, state-name, and fips-state-county-code.
4. The emissions data is merged with fips and states data, so that further mining and analysis can be done at state and county level. 
5. The data is then summarized at various levels to improve the performance of queries and plots in the web app. 
6. The data-frames are backed up into rds files in `data` sub-directory for faster loading at the start of `server.R`. 
  
#### B. Application Development
  
**Server side**:
  
1. At the start of the server (server.R), the data-frames are loaded from rds files in `data` sub-directory for faster loading at the start of `server.R`
2. Functions to plot choropleth US map and state map with color-shades are created using `map` library 
    + quartileStateUSMap() ## function to show states on US map with color based on quartile
    + quartileCountyMap('NY') ## function to show counties of a state with color based on quartile
3. A plot for US map at state level with color based on quartile is created (main US map on side-panel)
4. Based on the user selected state-code, a state level map is plotted using `map` library with counties color-coded based on their quartile. (state map on side panel below state-code)
5. A plot showing the total emissions for the state is generated using `ggplot` package. An additional  line is plotted to show the projected **Trend of Emissions**, with **linear regression model** for the state. (And displayed as the first plot on main-panel)
6. Another chart is created to show the **Emissions in the counties** within the state using `plotly` package. It is color-coded to show the different emission sources. (And displayed as the second chart on main panel)
7. A data-table is populated with latest emissions at the county level for the selected state and displayed on **Emissions Data** tab.  
8. Another data-table is populated with all emissions data at the county level for all states and displayed on **All Data** tab.  
 

**User side**:
  
1. User Interface is developed with a sidebar panel and main panel in fluidpage style.
2. The sidebar layout is populated with 
    + an one-liner about the app, 
    + US map at state level with color based on quartile, 
    + a selecter with all state-codes for the user to pick,
    + and state map at county level with color based on quartile
3. The main panel is layed out with multiple tabs
4. The first tab on main panel **Emissions Analysis** is populated with  
    + a plot (ggplot) showing the total emissions over years and a linear model line
    + a plotly chart to show emissions by counties and source
    + and linear regression model information
5. The second tab **Emissions Data** is populated with latest emissions at the county level for the selected state.
6. The third tab **All Data** is populated with latest emissions at the county level for all states.
7. The fourth tab **Documentation** is populated with instructions rendered from a markdown document
8. The last tab **What is the receipe?** is populated with documentation about the steps taken to develop the application rendered from a markdown document
  
#### C. Code:
  
1. Script for initial raw data load and creation of backup files - ./code/initialDataLoad.R
2. Script for loading backup (rds) files at the start of app server(server.R) - ./code/data.R
3. Script for functions to create US map and state map with color-shades - ./code/functions.R
4. server side script - server.R
5. User side script - user.R
6. User instruction on how to use the app - instructions.md 
7. Documentation that outlines the steps - readme.md 
  
  
## Deliverables
  
* Shiny Web Application : https://snrajesh.shinyapps.io/OneClickPM25Emissions
* Presentation (Rpresenter) : http://rpubs.com/snrajesh/DP20151122
* Code : https://github.com/snrajesh/OneClickPM25Emissions  
  

