Representation: </br>
![alt_text](https://github.com/arjuaman/Pagerank_of_my_capstone_project/blob/master/Capture2.jpg)

I worked on the data from: https://www.tdcj.texas.gov/death_row/dr_executed_offenders.html 
My aim was to get a list of all the last statements by those who were executed and then make a WordCloud visualization of the most often words by them, WITHOUT using the wordcloud or NLP libraries.
I put the conditions being that length of words should be greater than 5, other way could have been using wordcloud library and using the stopwords method from NLP library. 
I started with spidering the data from the site,using and modifying the spider.py file from code3, used BeautifulSoup for the anchor tags ,and then again for the consequent paragraph tags, put them into a list and consequently wrote into a file. I imported that file in a datagram, cleaned it and exported it to statements.csv, which helped me in converting to sqlite. Then I modified gword.py file to get the visualization. 

Simple Python Search Spider, Page Ranker, and Visualizer

This is a set of programs that emulate some of the functions of a search engine.  They store their data in a SQLITE3 database named
'spider.sqlite'.  This file can be removed at any time to restart the process.   

You should install the SQLite browser to view and modify the databases from:

http://sqlitebrowser.org/

This program crawls a web site and pulls a series of pages into the database, recording the links between pages.

Note: Windows has difficulty in displaying UTF-8 characters in the console so for each console window you open, you may need to type the following command before running this code:

    chcp 65001

http://stackoverflow.com/questions/388490/unicode-characters-in-windows-command-line-how


Run spider.py

Enter web url or enter: https://www.tdcj.texas.gov/death_row/dr_executed_offenders.html 

If you restart the program again and tell it to crawl more pages, it will not re-crawl any pages already in the database.  Upon 
restart it goes to a random non-crawled page and starts there. So each successive run of spider.py is additive.

Run spider.py

Enter web url or enter: https://www.tdcj.texas.gov/death_row/dr_executed_offenders.html 

You can have multiple starting points in the same database within the program these are called "webs". The spider chooses randomly amongst all non-visited links across all the webs.

If you want to dump the contents of the spider.sqlite file, you can run spdump.py

Run spdump.py

The spdump.py program only shows pages that have at least one incoming link to them.

Once you have a few pages in the database, you can run Page Rank on the pages using the sprank.py program.  You simply tell it how many Page Rank iterations to run.

Run sprank.py 

You can dump the database again to see that page rank has been updated:

Run spdump.py 

You can run sprank.py as many times as you like and it will simply refine the page rank the more times you run it. You can even run sprank.py a few times and then go spider a few more pages sith spider.py and then run sprank.py to converge the page ranks.

If you want to restart the Page Rank calculations without re-spidering the web pages, you can use spreset.py

Run spreset.py 

Run sprank.py 


For each iteration of the page rank algorithm it prints the average change per page of the page rank. The network initially is quite 
unbalanced and so the individual page ranks are changing wildly. But in a few short iterations, the page rank converges. You should run prank.py long enough that the page ranks converge.

If you want to visualize the current top pages in terms of page rank, run spjson.py to write the pages out in JSON format to be viewed in a web browser.

Run spjson.py 


Open force.html in a browser to view the visualization

You can view this data by opening the file force.html in your web browser. This shows an automatic layout of the nodes and links.  You can click and drag any node and you can also double click on a node to find the URL that is represented by the node.

This visualization is provided using the force layout from:

http://mbostock.github.com/d3/

If you rerun the other utilities and then re-run spjson.py - you merely
have to press refresh in the browser to get the new data from spider.js.

Comments are welcome.
