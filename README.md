# Selfoss-WF on Docker
This is a docker compose for Selfoss(https://github.com/fossar/selfoss) and my Selfoss-Webfront(https://github.com/MatthK/Selfoss-Webfront) all packaged together ready to go.

## Features
- A robust RSS solution to get content into a database
- A responsive newsite styled webfront to read your news
- Conveniently packaged into a single docker compose 

## Installation

1. Clone this repository with `git clone https://github.com/MatthK/swfd && cd swfd`
2. Adjust the defined database/username/password in the `nano docker-compose.yml`
3. Type `docker-compose up -d` to fire up the containers 
4. Update the database/username/password in the config.ini
   `sudo nano /var/lib/docker/volumes/swfd/bs/_data/config.ini`
5. Go to http://ip-address:8080/ to get to the Selfoss interface and create your RSS feeds. 
   The tags defined have to match the categories in the next point. You must have 11 different tags. Multiple feeds can be defined for one tag.
6. Update the database/username/password in the constants.php and based on the feeds and tags you have defined, adjust the 11 categories
   `sudo nano /var/lib/docker/volumes/swfd/wf/_data/constants.php`
7. Go once to http://ip-address/cfn.php to create a required function in the database
8. Optional, put a Reverse proxy in front # to give it a nice domain name
9. Enjoy

## Credits
The docker is based on Pamplemousse/dockerfiles(https://github.com/Pamplemousse/dockerfiles/tree/master/selfoss) which created a standalone Selfoss docker. I added my instance of the webfront and packaged it with a MySQL database to get it all in one package.
