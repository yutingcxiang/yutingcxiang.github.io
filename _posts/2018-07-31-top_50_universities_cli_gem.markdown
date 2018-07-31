---
layout: post
title:      "Top 50 Universities CLI Gem"
date:       2018-07-31 23:14:50 +0000
permalink:  top_50_universities_cli_gem
---


Since education had been on my mind lately with talks of starting college or going back to university for a master's degree, it got me thinking about the top colleges in the U.S. in 2018. A bit googling led me an up-to-date list located at https://www.thebestcolleges.org/rankings/top-50/. 

With this university list in mind, I set out to create a University CLI app that would display a ranked list of the top 50 schools in the US. The user is given an option to see further details about the university by selecting its rank and can view info such as location, a short description, and the school website for further details.

After receiving the green light on my project as well as assurance the website would be easy to scrape, I proceeded to follow along with Avi's video walkthrough of his daily-deal CLI app. Going into the project, I was most worried about setting up the environment and related files. Luckily, bundler was very straightforward and there weren't any major roadblocks there (except for installing the required gems locally).

The toughest part of the entire project turned out to be the scraper itself. After the usual scraping methods were turning up blanks, I reached out to the Flatiron team for assistance. After a couple of debugging sessions, it turns out the scraper was unable to pick up the data due to the JavaScript triggers for the collapsible college elements (a click was required to expand the field for more data). 

![ ](https://imgur.com/LOl0vgT)

I was then given a choice to either: 1) use a headless browser solution in the form of capybara, poltergeist and phantomjs or 2) to switch to a much simpler website. At that point, I had never heard of a headless browser and capybara was just a giant rodent to me.  But here's a simple explanation (from the first link below): 

> Capybara is a testing system, designed to be able to use a web browser like a real user would, but automatically. It is used to help find errors in "web apps" (websites like Refuge Restrooms), simulating the way a human tester would find them.
PhantomJS is a web browser, using the Webkit browser engine (the core part of Safari). It runs from the command-line, without showing a browser window.
Poltergeist allows Capybara to interact with PhantomJS. Capybara has a standardized way to do tests, which Poltergeist is designed to understand. Poltergeist also knows how to translate these tests to a way that PhantomJS will understand.
All together: Capybara tells Poltergeist what to do, Poltergeist tells PhantomJS what to do. This way, our site gets tested in a real browser (somewhat like Safari), automatically.

Even so, it took a two hour debugging session with a technical coach to properly setup the session for viewing the hidden JS fields on the page. First we had find a way to trigger the expand all button on the page to view the college descriptions for all 50 colleges (on load, the page only had the first five shown by default). Once that was done, we were able to scrape the relevant fields in a similar matter to Nokogiri using the css selectors. 

Despite this huge success, there were two minor issues to point out. First, there was an issue with my terminal printing out the console log messages on the web page, which got mixed up with my CLI interface. This was solved by outputting the messages to an instanced phantomjs logger instead. The second issue is a delay in outputting the scraped results (typically takes a few seconds to process). I don't currently have a solution for the performance issue but definitely something I can explore once I'm more experienced.

Overall, this has been quite the learning experience. Although the project took much longer than anticipated (and I ultimately did not end up using open-uri and nokogiri at all), I was able to get some exposure to a testing framework and learned a bit about headless browsers, both of which were material that were beyond the scope of the project or any prior lessons. I am definitely glad I stuck with this project and expanded my learning with the process. 

If you are interested in learning more about capybara, phantomjs, and poltergeist, below are the resources I used for my project:

1. https://github.com/RefugeRestrooms/refugerestrooms/wiki/What-is-Capybara%3F-What-is-PhantomJS%3F-What-is-Poltergeist%3F
2. https://github.com/teampoltergeist/poltergeist
3. https://readysteadycode.com/howto-scrape-websites-with-ruby-and-poltergeist
4. http://tutorials.jumpstartlab.com/topics/scraping-with-capybara.html
5. https://www.coursera.org/lecture/photo-tourist-web-app-capstone/poltergeist-phantomjs-headless-webdriver-G1RmB


