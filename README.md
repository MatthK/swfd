# Selfoss-WF on Docker
This is a docker compose for [Selfoss](https://github.com/fossar/selfoss) and my [Selfoss-Webfront](https://github.com/MatthK/Selfoss-Webfront) all packaged together ready to go.

## Features
- A robust RSS solution to get content into a database
- A responsive newsite styled webfront to read your news
- Conveniently packaged into a single docker compose 
- It should now also work on both arm64 and amd64 platforms

## Installation

1.  Clone this repository with `git clone https://github.com/MatthK/swfd && cd swfd`
2.  Adjust the defined database/username/password in the `nano docker-compose.yml`
    You might also have to replace the image with `matthk72/selfoss-wf:latest-amd64` (just add the -amd64) in case you don't use a Raspberry Pi
3.  Type `docker-compose up -d` to fire up the containers 
3.  Wait till the database has initialized. Then stop the containers again with `docker-compose down`
3.  Update the database/username/password in the `nano swfd/bs/config.ini` and copy paste the whole content into the file on the docker volume
    `sudo nano /var/lib/docker/volumes/swfd_bs/_data/config.ini`
5.  Start the containers again with `docker-compose up -d`
6.  Go to <http://ip-address:8080/> to get to the Selfoss interface and create your RSS feeds
    The tags defined have to match the categories in the next point. You must have 11 different tags. Multiple feeds can be defined for one tag. Either manually refresh the sources, or wait 15 minutes till the next cron job picks it up
7.  Update the database/username/password in the constants.php and based on the feeds and tags you have defined, adjust the 11 categories
    `nano swfd/wf/constants.php`
8.  Go once to <http://ip-address/cfn.php> to create a required function in the database. After that, you can access your personal newspaper at http://ip-address/
9.  Optional, put a Reverse proxy in front # to give it a nice domain name
10. Enjoy

## Sample feeds

Below are some of the feeds I am using. Be aware that some work a bit better than others, and the more active ones (BBC, Yahoo, CNBC) tend to drown the ones with more quality stuff but that update less often. Some content gets nicely fully downloaded, some feeds don't work so well and only teasers get retrieved or the formatting is a bit off.

Many feeds have also other categories available, simply look at the URLs and see how you could possibly modify them to find an overview page, or just with trial and error.

### English Feeds

| Feed	| Category 	| Comment |
|---	|---	|---	|
| [Airway](https://www.airway1.com/feed/)	| Aviation	|  |
| [Airways Magazine](https://airwaysmag.com/rss)	| Aviation	|	|
| [AsiaTimes](https://asiatimes.com/category/world/feed/)	| World	|	|
| [AsiaTimes](https://asiatimes.com/category/china/feed/)	| China	| (there are many categories, just adapt according to your interest) |
| [AutoSport](https://www.autosport.com/rss/feed/f1)	| Sport |	|
| [BBC News](http://newsrss.bbc.co.uk/rss/newsonline_uk_edition/world/rss.xml)	| World	| (see https://www.bbc.co.uk/news/10628494#userss for different feeds) |
| [BGR](https://bgr.com/feed/)	| Technology	| |
| [Channel News Asia](https://www.channelnewsasia.com/rssfeeds/8395744)	| Asia | |
| [CNBC](https://www.cnbc.com/id/100727362/device/rss/rss.html)	| World | (International) |
| [CNBC](https://www.cnbc.com/id/20910258/device/rss/rss.html)	| Business | |
| [CNBC](https://www.cnbc.com/id/10000739/device/rss/rss.html)	| Travel | |
| [CNBC](https://www.cnbc.com/id/19832390/device/rss/rss.html)	| Asia | |
| [CNBC](https://www.cnbc.com/id/19794221/device/rss/rss.html)	| World | (Europe) |
| [CNBC](https://www.cnbc.com/id/10001147/device/rss/rss.html)	| Business | |
| [CNBC](https://www.cnbc.com/id/19854910/device/rss/rss.html)	| Technology | |
| [Engadget](http://www.engadget.com/rss.xml)	| Technology | |
| [FIA](https://www.fia.com/rss/news)	| Sport | |
| [HKG Living](https://hongkongliving.com/feed/)	| HKG | |
| [IBT](https://www.ibtimes.sg/rss/world)	| World | they have various categories like sports/science/technology |
| [Leeham News](https://leehamnews.com/feed/)	| Aviation | |
| [Little white lies](https://lwlies.com/feed/)	| Film | |
| [Movieweb](https://movieweb.com/rss/movie-reviews/)	| Film | |
| [NASA](https://www.nasa.gov/rss/dyn/lg_image_of_the_day.rss)	| Science | |
| [Nature](http://feeds.nature.com/nature/rss/current)	| Science | |
| [Out of Town](https://outoftownblog.com/feed/)	| Travel | |
| [Politico](http://rss.politico.com/politics-news.xml)	| World	| [Economy](http://rss.politico.com/economy.xml), [Defense](http://rss.politico.com/defense.xml) |
| [RT](https://www.rt.com/rss/)	| World | |
| [RTHK](http://rthk.hk/rthk/news/rss/e_expressnews_elocal.xml)	| HKG | |
| [Science Daily](http://feeds.sciencedaily.com/sciencedaily)	| Science | |
| [SCMP](https://www.scmp.com/rss)	| Various | (most content is paid, with some free stuff. It only loads teasers here) |
| [Seattle Times](https://www.seattletimes.com/boeing-aerospace/feed/)	| Aviation | |
| [TechRadar](https://www.techradar.com/rss)	| Technology | |
| [The Intercept](https://theintercept.com/feed/?lang=en)	| World | |
| [VoxEU](https://voxeu.org/feed/recent/rss.xml)	| Business | |
| [Wired News](http://www.wired.com/news_drop/netcenter/netcenter.rdf)	| Technology | |
| [Yahoo News](http://rss.news.yahoo.com/rss/world)	| World | |

### German Feeds

| Feed	| Category 	| Comment |
|---	|---	|---	|
| [aeroTelegraph](https://www.aerotelegraph.com/feed)	| Aviation	| |
| [Blick](https://www.blick.ch/rss.xml)	| Swiss	| |
| [Formula 1](https://www.motorsport-total.com/rss/rss_formel-1.xml)	| Sport	| |
| [SRF](https://www.srf.ch/sport/bnf/rss/2958)	| Sport	| |

## Credits
The docker is based on [Pamplemousse/dockerfiles](https://github.com/Pamplemousse/dockerfiles/tree/master/selfoss) which created a standalone Selfoss docker. I added my instance of the webfront and packaged it with a MySQL database to get it all in one package.