# GSoC Final Report

##### Organization : International Neuroinformatics Coordinating Facility (INCF)

##### Project      : Automated comparison of scientific methods for time series analysis.

##### Student      : Diptanshu Mittal

##### Mentors      : Ben Fulcher, Oliver Cliff

### Introduction

In this **Google Summer of Code 2021** project I continued the development of *Comp-Engine-Features*, an online-platform
that helps the user to compare new time-series analysis algorithms to a collection of over 7700+ existing algorithms in
the [_hctsa_ package](https://github.com/benfulcher/hctsa). The portal takes a new time-series analysis algorithm (as
python/julia code) from the user and computes its outputs across
a [dataset of 1000 diverse time series](https://figshare.com/articles/1000_Empirical_Time_series/5436136). It then
analyzes the spearman correlation between the output of the user's algorithm with the _hctsa_ feature library and
presents a range of intuitive output visualizations that show the best-matching features. This output allows any new
method to be automatically benchmarked against interdisciplinary literature and helps the user to understand connections
between their algorithm and the existing interdisciplinary time-series analysis algorithms, and therefore to assess
whether their algorithm is really contributing to the genuine advancement of the field.

Here are a few examples of the platform functionality I developed in this GSoC project:
![](GIF-200822_154754.gif)
![](GIF-200822_154754.gif)

### What was done

The development process of the project can be broken down into three parts:

1. **First phase - Upgrading to API-first architecture**  
   &nbsp; _In this phase, I worked on upgrading the platform architecture by introducing a range of changes:_

    * The front-end was developed as a SPA from scratch using React framework. Development of components for 'Home', '
      How-it-works', 'Contact', 'Preloader', 'Result', 'Syntax error', 'Timeout Error', '404 Not found', 'Navigation
      Bar', 'Explore' etc.
    * Front-end was connected to the backend server using APIs.
    * New views were created to return JsonResponse for API calls.
    * NoSQL database was created for storing precomputed correlation and p-values for various features in hctsa package
      and for storing empirical 1000 time-series and their categories.
    * Redux store was developed in the React to cache the explored hctsa features, time-series and network plots.
    * Added the search functionality in the navigation bar.


2. **Second phase - Improving the output visualizations**  
   &nbsp; _In this phase, I focused on improving the output visualizations, that will help the user to understand
   connections between the feature being explored and other hctsa features. A range of output visualizations were
   developed from scratch in React app, including:_
    * Interactive results table (functionality shown in the gif below), that allows users to:
        * Columns button to show / hide column from table.
        * Filter buttons to filter the rows based in column data.
        * Density button to change the height of the rows.
        * Download all results in .csv format.
    * Visualization of top feature results as interactive scatter plots (as visualized in the gif below), which enables
      users to:
        * Select the no. of scatter plots using interactive slider.
        * Switched between rank-vs-raw data points.
        * Hover to see data points and time-series names.
        * Zoom each plot to more clearly visualize the relationships.
    * Visualization for comparing two features using category plots (as visualized in the gif below), which enables
      users to:
        * Select the feature from drop down list.
        * Switched between rank-vs-raw data points.
        * Compare the features based on the category of time series.
        * Click on the data points to visualize the time series corresponding to that datapoint.
        * Zoom each plot to more clearly visualize the relationships.
    * Network visualization for pairwise relationships between each of the top 15 features matching the center feature(
      black node), which enables users to:
        * Click on the node to get feature name and keywords.
        * Double-click on a feature to centralize that feature.
        * Hover over nodes to get feature name and over edges to get the correlation.
        * Recenter button to go back to center feature at the start.
        * Legends to get pairwise relationship in a glance.
        * Toggle buttons to control the network plots canvas.


3. **Third phase - Adding docker to improve security and deploying the system on a server.**  
   &nbsp; _This phase was one of the most challenging one. In this phase, we:_

    * Integrated docker with the Django backend and shifted code computation to docker containers.
    * Added support for Python and Julia code computation.
    * Deployed the complete system on the Sydney University server.

### Link to work

* [Link to full repository](https://github.com/NeuralSystemsAndSignals/Comp-Engine-Features)
* [Links for all commits]()
* [Link to all weekly reports]()

### Future Work

All the requirements outlined in the GSoC proposal have been completed. This project act like a stepping stone in the
development of _Comp-Engine-Features_. After the official GSoC period, I plan to contribute to this further development
by:

* Creating a contribution section using which users can contribute their time-series analysis features.
* Creating a python package using which users can get the raw data and visualize in their own way.
