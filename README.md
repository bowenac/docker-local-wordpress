# Docker Local Wordpress Development

Local WordPress development environment with Docker and Docker Compose.

This will create 4 containers

-   WordPress
-   WP-CLI
-   phpMyAdmin
-   MySQL

I use Docker Desktop for Windows and this has worked well.

I have also been playing around with [portainer.io](https://www.portainer.io/) for managing docker containers, which seems pretty cool but not needed here.

## Requirements

Make sure you have [**Docker**](https://www.docker.com/) installed.

Clone this repository or just copy docker-compose.yml and the .env file into your new project folder.

## Config

Edit the .env file to change the following variables to your prefernce.

-   IP
-   PROJECT_NAME
-   DB_ROOT_PASSWORD
-   DB_NAME

## Install

Open a terminal where you cloned the respository, or just open the folder in your IDE and use it's terminal... Yay for VSCODE.

Run

`docker-compose up -d`

You should now see two new folders inside your project folder.

-   wordpress_files
-   db_data

The containers are now built and running.

You should be able to access both WordPress, and phpMyAdmin installations with the configured IP in the browser address. By default it is `http://127.0.0.1`

-   Access WordPress [http://127.0.0.1](http://127.0.0.1)
-   Access phpMyAdmin [http://127.0.0.1:8080](http://127.0.0.1:8080) user root, password you set in .env

## Stop Container

Like other containers just run the following, or if you're using portainer.io you can stop/start your containers from there.

`docker-compose down`

## WP CLI

To use WP CLI just run the following from your project in terminal

`docker-compose run --rm wpcli bash`

After that you can use regular WP CLI commands.

**List of useful commands**

View WordPress Info

`wp --info`

View WP CLI version

`wp --version`

View list of installed plugins

`wp plugin list`

View list of installed themes

`wp theme-list`

Runs a search/replace on the database and shows a report but does not save/export a database backup file.

`wp search-replace 127.0.0.1 https:example.com --dry-run`

Runs a search/replace on the database and creates sql backup file, in this case it would be database.sql, and would be stored in the wordpress_files directory.

`wp search-replace 127.0.0.1 https:example.com --all-tables-with-prefix --export=database.sql`
