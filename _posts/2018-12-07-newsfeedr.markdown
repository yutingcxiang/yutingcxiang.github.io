---
layout: post
title:      "NewsFeedr "
date:       2018-12-07 22:41:26 +0000
permalink:  newsfeedr
---


For my final project, I created my own new feed application, Newsfeedr. The application was built with a Rails API backend and React/Redux frontend, with the data from [News API](https://newsapi.org/). 

This application was a great way for me to test my skills at implementing some new website features.

<a href="https://imgur.com/dZcEbl6"><img src="https://i.imgur.com/dZcEbl6l.png" title="source: imgur.com" /></a>

<br>

**Feature 1: Rails API Backend**

The application was built with a Rails API backend, which is slightly different from the previous Rails applications. The API version is simpler and more lightweight, without the views, helpers, and other unneeded parts. The main purpose of my backend involved fetching data from the News API using the Faraday gem. My routes were set up to receive inputs from the user as params and submitted them as a search query to the API.

With the use of the Foreman gem and a Procfile, the application was configured to have the API running on http://localhost:3001/ and the frontend running simultaneously on http://localhost:3000/. This allowed fetch requests from React to retrieve data from Rails. Additionally, the entire app can be started with `rake start` (after installing dependencies).

<a href="https://imgur.com/x3WR78x"><img src="https://i.imgur.com/x3WR78xl.png" title="source: imgur.com" /></a>

<br>

**Feature 2: React Front End**

The frontend was built with several React containers and components. The containers held the majority of the page logic and called upon the smaller components, which were mostly used for rendering lists, individual items, and layout pieces (like footers). 

Most of the styling of was done with [Semantic UI](https://semantic-ui.com/), a good alternative to react-bootstrap. There are multiple ways of setting this up (with using a CDN and linking the stylesheet in your index.html being the easiest), I mainly relied on the default theme with my own custom css added on top in my App.css file. 

It was a simple and fast way for me to add spacing, color, and different headers/buttons/labels, which greatly enhanced the look of the app.

<a href="https://imgur.com/ciCSgZR"><img src="https://i.imgur.com/ciCSgZRl.png" title="source: imgur.com" /></a>

<br>


**Feature 3: RESTful React Router **

Newsfeedr uses react-router to provide 3 different routes: one for recent headlines, one for browsing all news sources, and one for searching for specific articles. Additionally, I implemented nested routing and redirects for a more RESTful experience.

Nested routes display the source (ABC News) or the search query (ex: 'microsoft') in the route, which then gets passed to the back as a param (ex: params["query"]) and can be used by Faraday for fetching the relevant articles. 

<a href="https://imgur.com/dxWBym3"><img src="https://i.imgur.com/dxWBym3l.png" title="source: imgur.com" /></a>

Redirecting was also used to update the search url and to refresh the page to allow for multiple searches without having to come back to the page.

<a href="https://imgur.com/XqUFSpz"><img src="https://i.imgur.com/XqUFSpzl.png" title="source: imgur.com" /></a>

<br>

**Feature 4: Redux Store**

The application also incorporates Redux, which was used to manage the state of various components. The store held the results of the API calls (with redux-thunk) in arrays and even kept the last search query in memory. The various actions managed the different fetch requests and the reducers kept everything up to date in the store. 

Also incorporating the Redux devtools extensions made debugging the application a lot easier as it was very clear to see how the state changed from one page to another.

The only state not currently in the store is the pagination, but that is something I am looking into for the future.




