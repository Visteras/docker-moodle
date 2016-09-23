docker-moodle
=============

A Dockerfile that installs and runs the latest Moodle stable.

## Installation

```
git clone https://github.com/visteras/docker-moodle
cd docker-moodle
docker build -t moodle .
```

## Usage

To spawn a new instance of Moodle:

```
docker run -d --name DB -p 3306:3306 -e MYSQL_DATABASE=moodle -e MYSQL_USER=moodle -e MYSQL_PASSWORD=moodle centurylink/mysql
docker run -d -P --name moodle --link DB:DB -e MOODLE_URL=http://example.com:8080 -p 8080:80 jauer/moodle
```
I added new env: DB_ENV_TYPE_DB for change db type as mysqli/mariadb etc.

You can visit the following URL in a browser to get started:

```
http://example.com:8080
```

## Caveats
The following aren't handled, considered, or need work: 
* moodle cronjob (should be called from cron container)
* log handling (stdout?)
* email (does it even send?)

## Credits

This is a reductionist take on [sergiogomez](https://github.com/sergiogomez/)'s docker-moodle Dockerfile.

