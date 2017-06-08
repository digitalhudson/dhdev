# DHDEV site 0.1.2
The Digital Hudson Dev Site is a project created by Tim Moore for Woodstock based Digital Hudson.

Digital Hudson does some stuff. 


**DHDEV Site** is a web application based on:

* [Scala 2.11.8 as programming language](http://www.scala-lang.org/)
* [SBT 0.13.15 as build tool](http://www.scala-sbt.org/)
* [Play Framework 2.5.8 as web application framework](https://www.playframework.com/)
* [Play2-auth 0.14.2 as authentication module for Play](https://github.com/t2v/play2-auth/)
* [PostgreSQL 9.6 as database](http://www.postgresql.org)
* [Slick 3.1.1 as database access layer](http://slick.lightbend.com)
* [Slick-pg 0.14.1 extending slick for support PostgreSQL data types](https://github.com/tminglei/slick-pg)
* [Foundation 6.2.3 as front-end framework](http://foundation.zurb.com)

The application is a website where you have to login to enter in a restricted page. The restricted page is a messages
page, where you can see, add or delete messages that are shared between all the users. Also is possible to edit your
own user and, if you are an admin user, you can add other non admin users.


## Getting the project
As usual:

    you will be provided with that information

The following commands are written for a GNU/Linux environment (**Debian**, if you want to know). So please adapt it
to your system if it is necessary. Also they are run as if that you are located inside the folder `rmgdev`, the root of this project.

## Database

### Database setup
Check the [PostgreSQL website](http://www.postgresql.org/download/) for installation instructions.

Create a current installation, a user and a database:

    use psql and the ddl provided to you

**IMPORTANT!** If you change any database config value, please remember to update the config file
`conf/application.conf`

Next create the tables and add some data to the database using the script `conf/database.sql`

    get database.sql from DH admin
	sudo -u postgres psql -p 5432 -d dhdb -f conf/database.sql

This script will create sample data for files, the participants and their interactions for testing purposes.

### Database mapping code
The file `models.db.Tables.scala` contains the database mapping code. It has been generated running the main class
`utils.db.SourceCodeGenerator`. If you want to regenerate the database mapping code for any reason, check the
config file `conf/application.conf` and run:

    sbt tables

## SBT

To run the project execute:

    sbt run

And open a browser with the url [http://localhost:9000](http://localhost:9000)

The plugin [sbt-updates](https://github.com/rtimush/sbt-updates) is installed (see `plugins.sbt`). To check
if all the dependencies are up to date, it is necessary to execute:

    sbt dependencyUpdates

## License
Licensing conditions can be found in `LICENSE` file.
