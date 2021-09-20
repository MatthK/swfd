# Selfoss-WF on Docker
This is a docker compose for Selfoss(https://github.com/fossar/selfoss) and my Selfoss-Webfront(https://github.com/MatthK/Selfoss-Webfront) all packaged together ready to go. It even has some RSS feeds already included.

## Features
- A robust RSS solution to get content into a database
- A responsive newsite styled webfront to read your news
- Conveniently packaged into a single docker compose 

## Installation

1. Clone this repository with `git clone https://github.com/MatthK/swfd && cd swfd`
2. Adjust the defined database password in these three files (`nano sf-bs/config.ini`, `nano sf-wf/constants.php`, `nano docker-compose.yml`)
3. Optional, delete the database files in `sf-db` if you want to have an empty database (it will be recreated automatically once you open Selfoss at point 4). 
3. Type `docker-compose up -d` to fire up the containers 
4. Go to http://ip-address:8080/ to get to the Selfoss interface and adjust the RSS feeds or create your own. 
   (The tags defined have to match the categories in the next point. You must have 11 different tags. Multiple feeds can be defined for one tag.)
5. Based on the feeds and tags you have defined, adjust the constants.php and replace/adjust the 11 categories
6. If you deleted the database, go once to http://ip-address/cfn.php to create a required function in the database
7. Optional, put a Reverse proxy in front # to give it a nice domain name

Enjoy

## Credits
The docker is based on Pamplemousse/dockerfiles(https://github.com/Pamplemousse/dockerfiles/tree/master/selfoss) which created a standalone Selfoss docker. I added my instance of the webfront and packaged it with a MySQL database to get it all in one package.
