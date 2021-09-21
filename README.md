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

English Feeds

Airway				Aviation		https://www.airway1.com/feed/
Airways Magazine	Aviation		https://airwaysmag.com/rss
AsiaTimes			World			https://asiatimes.com/category/world/feed/
AsiaTimes			China			https://asiatimes.com/category/china/feed/  (there are many categories, just adapt according to your interest)
AutoSport			Sport			https://www.autosport.com/rss/feed/f1 (Formula 1)
BBC News			World			http://newsrss.bbc.co.uk/rss/newsonline_uk_edition/world/rss.xml  (see https://www.bbc.co.uk/news/10628494#userss for different feeds)
BGR					Technology		https://bgr.com/feed/
Channel News Asia	Asia			https://www.channelnewsasia.com/rssfeeds/8395744
CNBC				World			https://www.cnbc.com/id/100727362/device/rss/rss.html (International)
CNBC				Business		https://www.cnbc.com/id/20910258/device/rss/rss.html
CNBC				Travel			https://www.cnbc.com/id/10000739/device/rss/rss.html
CNBC				Asia			https://www.cnbc.com/id/19832390/device/rss/rss.html
CNBC				World			https://www.cnbc.com/id/19794221/device/rss/rss.html (Europe)
CNBC			    Business		https://www.cnbc.com/id/10001147/device/rss/rss.html
CNBC				Technology		https://www.cnbc.com/id/19854910/device/rss/rss.html
Engadget			Technology		http://www.engadget.com/rss.xml
FIA					Sport			https://www.fia.com/rss/news
HKG Living			HKG				https://hongkongliving.com/feed/
IBT					World			https://www.ibtimes.sg/rss/world  they have various categories like sports/science/technology 
Leeham News			Aviation		https://leehamnews.com/feed/
Little white lies	Film			https://lwlies.com/feed/
Movieweb			Film			https://movieweb.com/rss/movie-reviews/
NASA				Science			https://www.nasa.gov/rss/dyn/lg_image_of_the_day.rss
Nature				Science			http://feeds.nature.com/nature/rss/current
Out of Town			Travel			https://outoftownblog.com/feed/
Politico			World			http://rss.politico.com/politics-news.xml    or http://rss.politico.com/economy.xml http://rss.politico.com/defense.xml
RT					World			https://www.rt.com/rss/
RTHK				HKG				http://rthk.hk/rthk/news/rss/e_expressnews_elocal.xml
Science Daily		Science			http://feeds.sciencedaily.com/sciencedaily
SCMP				Various			https://www.scmp.com/rss (most content is paid, with some free stuff. It only loads teasers here)
Seattle Times		Aviation		https://www.seattletimes.com/boeing-aerospace/feed/
TechRadar			Technology		https://www.techradar.com/rss
The Intercept		World			https://theintercept.com/feed/?lang=en
VoxEU				Business		https://voxeu.org/feed/recent/rss.xml
Wired News			Technology		http://www.wired.com/news_drop/netcenter/netcenter.rdf
Yahoo News			World			http://rss.news.yahoo.com/rss/world

German Feeds

aeroTelegraph		Aviation		https://www.aerotelegraph.com/feed
Blick				Swiss			https://www.blick.ch/rss.xml
Formula 1			Sport			https://www.motorsport-total.com/rss/rss_formel-1.xml
SRF					Sport			https://www.srf.ch/sport/bnf/rss/2958


## Credits
The docker is based on [Pamplemousse/dockerfiles](https://github.com/Pamplemousse/dockerfiles/tree/master/selfoss) which created a standalone Selfoss docker. I added my instance of the webfront and packaged it with a MySQL database to get it all in one package.
