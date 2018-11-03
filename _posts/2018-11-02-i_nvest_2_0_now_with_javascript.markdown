---
layout: post
title:      "i.nvest 2.0 (Now with JavaScript!)"
date:       2018-11-03 03:37:02 +0000
permalink:  i_nvest_2_0_now_with_javascript
---


After completing the JavaScript portion of the curriculum, I refactored my Rails project and updated the interface. The new and improved i.nvest now includes a cleaner and more dynamic look with the addition of ajax. 

![i.nvest Welcome Page](https://imgur.com/P3FXRCw)

This allowed me to combine views as well as hide large lists for better navigation. Additionally, users can easily click through lists and submit forms without refreshing, leading to a much better user experience.


**User Home Page**

The biggest change was the user Home page. Previously, the page displayed all of user's funds and portfolios. Now it also includes a form at the bottom for creating a new investment. Upon submission, a new line is added to the investment table with the submitted info. Users no longer have to navigate to a separate page to fill out a form and then get redirected back to their Home page to see this change. Everything is loaded dynamically via ajax.

![i.nvest User Home Page](https://imgur.com/pEb5SjT)


**Integrate IEX API**

Another major update to the site involves the integration of API data from IEX (a national stock exchange) with a fantastic and comprehensive free API platform for developers to access a wealth of stock market data. Since my application has provides a list of funds for users to explore, I decided to pull stock quotes from IEX to extract the company name, fund sector, and latest listing price to provide up-to-date info for my users.

This was done in the controller through the 'net/http' and 'uri' gems. I saved the data as JSON and assigned the information as attributes to my fund model. Below is an example quote for Twitter. 

![IEX Twitter Quote](https://imgur.com/DEorwyW)

Check out their developer site for more info: https://iextrading.com/developer/


**Dynamic Pages**

Finally, with all the new fund data from the IEX API, I decided to update the funds listings. The index page is combined with my scoped route for displaying the top funds at the top. Users can click on the fund to be redirected to the fund's show page with the API data. 

![i.nvest Show Page for AAPL](https://imgur.com/mk8eaWe)

The bottom of the page includes 'previous' and 'next' buttons to allow users to flip through all of the available funds (all rendered with ajax). 


**Next Version**

Although i.nvest 2.0 is a much better improvement over the original i.nvest Rails-only app, I would love to continue improving the functionality. For i.nvest 3.0 I am already planning to integrate a search function to allow users to look up info for specific funds they have in mind (with data from IEX) as users are currently limited to the funds they create (plus the original seed funds). 

![Trading Floor With Usher](https://media.emirates247.com/images/2013/07/ashur1.jpghttp://)




