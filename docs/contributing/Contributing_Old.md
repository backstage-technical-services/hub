## Working locally

Working locally is more complicated, but allows you to work on the code
and test it before pushing any changes to the repository.

### Docker

We use [Docker][link-docker] to configure and run the site locally; make
sure you've installed [Docker][link-docker-install] and [Docker
Compose][link-docker-install-compose] before continuing.

It's recommended you are familiar with the following:

* [Images and containers][link-docker-images-vs-containers]
* [Running containers][link-docker-container-run]
* [Executing commands in containers][link-docker-container-exec]
* [Docker compose][link-docker-compose]

If you want to learn more, Docker's documentation is fantastic:

* [Docker][link-docker-docs]
* [Docker Compose CLI][link-docker-docs-compose-cli]
* [Docker Compose Files][link-docker-docs-compose-file]

> **Windows and macOS users beware:**
>
> Neither Windows 10 nor macOS offer true native containerisation
> support (and macOS offers none at all). This means that in order to
> function, Docker for Windows and Docker for Mac need to run a Linux
> VM, which is what actually runs the containers. This VM has an
> additional RAM footprint of about 4GB, so make sure you have plenty of
> RAM.
>
> Because of this VM, the use of volumes (which is how we enable
> "hot-reloading" during development), can result in very long load
> times, making the site practically impossible to use.
>
> If you experience this, I recommend you manually run a Linux VM for
> both docker, the project files and your IDE. Windows 10 users can now
> run some aspects of Ubuntu natively (see
> [below](#ubuntu-support-windows-only)), but I have no experience with
> this so you're on your own.
>
> Alternatively, dual boot with Linux (Ubuntu is incredibly easy to
> use). You may well find you prefer it ...

### Install an IDE

You are welcome to use whatever IDE you choose, but we recommend
PhpStorm by Jetbrains - it's industry leading and free for students!

### Ubuntu support (Windows only)

If you're developing on Windows, you can get by with plain old Windows,
but we recommend you add the "Windows Subsystem for Linux" - this allows
you to run Ubuntu almost natively within Windows.

This will let you use the included scripts to help with development.

See the [docs from Microsoft][link-windows-linux-support] for more
information.

### Installing the site

Once you have the above configured, you can install the site:
1. Clone the repository

   ```sh
   $ git clone git@github.com:backstage-technical-services/laravel-site.git
   ```
2. Create the environment file from the example file

   ```sh
   $ cp .env.example .env
   ```
3. Populate the environment file

   > If you're using Docker, most of the environment variables are
   > populated for you. All you need to do are generate the site key
   > (see [below](#some-helpful-commands)) and grab the rest from a
   > member of the team.

### Running the site

The docker set-up includes the following services:

* A combined Nginx and PHP-FPM service to serve the website
* MariaDB database
* Mail server

To start everything up, all you need to do is run

```sh
$ .docker/local/bin/start.sh
```

> The first time you run this Docker will need to download the relevant
> image layers; this may take a while but this is a one-time thing
> (well, until the images are updated).

> The first time you boot the database, it will need to initialise
> itself and will restart a couple of times before it's ready to be
> used.

To stop everything, it's

```sh
$ .docker/local/bin/stop.sh
```

### Some helpful commands

Here are some helpful commands for interacting with the PHP container:

* Generate an app key:

  ```sh
  $ docker exec bts_site sh -c "php artisan key:generate"
  ```

* Run any database migrations:

  ```sh
  $ docker exec bts_site sh -c "php artisan migrate"
  ```

* View the logs:
  * Nginx and PHP:

    ```sh
    $ docker logs bts_site
    ```
  * Database:

    ```sh
    $ docker logs bts_mysql
    ```

* Pull any changes from the repository and update any assets

  ```sh
  $ .docker/local/bin/update.sh
  ```

* Continually re-build assets when they change

  ```sh
  $ .docker/local/bin/watch-assets.sh
  ```

You can enter the container with an interactive bash shell with

```sh
$ docker exec -ti bts_site bash
```

From here, you can run any command as if you were in a normal terminal
session.

> Because the site uses a volume for the files, you can make changes
> either in your own operating system or in the container and they'll be
> reflected in the other. The only thing you can't do is run docker
> commands.

### Viewing emails

Included in the Docker set-up is a local SMTP server. This doesn't
actually send any emails, so you're free to test with any email address,
and provides a user interface for viewing any emails that have been
sent.

You can view this interface at
[http://localhost:8001](http://localhost:8001) (unless you've changed
the value of `PORT_MAIL` in your `.env` file).

### Connecting to the MySQL database

The MySQL database is exposed to your own computer so you can connect to
it using the editor of your choice:

* Host: `localhost`
* Port: `6001` (unless you've changed the value of `PORT_MYSQL` in your
  `.env` file)
* Username: `developer` (unless you've changed the value of
  `DB_USERNAME` in your `.env` file)
* Password: `developer` (unless you've changed the value of
  `DB_PASSWORD` in your `.env` file)

### Understanding the Website

The website is built using PHP 7, with a framework called Laravel; their
[documentation][link-laravel-docs] is the best place to start to
familiarise yourself with the organisation of the website.

It's also recommended you familiarise yourself with [SASS][link-sass] as
this is used to process the stylesheets.

## Development Workflow

See the [Development Workflow][link-workflow] document.

[link-laravel-docs]: https://laravel.com/docs/6.0
[link-sass]: https://sass-lang.com/guide
[link-workflow]: ./Development%20Workflow.md
[link-docker]: https://www.docker.com/
[link-docker-install]: https://docs.docker.com/install/
[link-docker-install-compose]: https://docs.docker.com/compose/install/
[link-docker-images-vs-containers]: https://stackoverflow.com/a/23736802
[link-docker-container-run]: https://docs.docker.com/engine/reference/commandline/container_run/
[link-docker-container-exec]: https://docs.docker.com/engine/reference/commandline/container_exec/
[link-docker-compose]: https://docs.docker.com/compose/
[link-docker-docs]: https://docs.docker.com/engine/reference/commandline/cli/
[link-docker-docs-compose-cli]: https://docs.docker.com/compose/reference/
[link-docker-docs-compose-file]: https://docs.docker.com/compose/compose-file/
[link-windows-linux-support]: https://docs.microsoft.com/en-us/windows/wsl/install-win10
