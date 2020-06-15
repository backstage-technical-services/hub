# Contributing - Developing

> Please make sure you have read the [main contribution
> guide][contributing-main] first and are familiar with the [development
> workflow][contributing-workflow].
>
> It would also be a good idea to familiarise yourself with [our
> tools][contributing-tools].

## Pre-requisites

Before you start developing, please make sure you have the following set
up on your computer.

> **Note:** While it is possible to use all of these tools and develop
> both the API and SPA on Windows, it is strongly recommended that you
> use a Linux VM or the Windows Subsystem for Linux in order to take
> advantage of the tooling we use to simplify some processes.

1. **SDKMAN**

   SDKMAN is a useful utility that makes it easy to install and manage
   Java SDKs. Follow [these instructions][install-sdkman] to install it.
   You can then install an SDK with the following command:

   ```sh
   $ sdk install java <version>
   ```

   This will install the SDK to `~/.sdkman/candidates/java`.

   You can search for available versions using `sdk search java` and set
   your default java version using `sdk default java <version>`.

2. **Node.js and Yarn**

   Node.js is needed in order to use and run the SPA; you can install
   the latest LTS (12.x) [here][install-nodejs].

   You will also need to [install Yarn][install-yarn], which is an
   improved version of npm, the node package manager.

3. **Docker and Docker Compose**

   In order to run any auxiliary services (eg, the SMTP server and
   database) you will need to have [Docker installed][install-docker],
   as well as [Docker Compose][install-docker-compose].

   It's recommended you are familiar with the following:

   * [Images and containers][docker-images-vs-containers]
   * [Running containers][docker-container-run]
   * [Executing commands in containers][docker-container-exec]
   * [Docker compose][docker-compose-docs]

   If you want to learn more, Docker's documentation is fantastic:

   * [Docker][docker-docs]
   * [Docker Compose CLI][docker-docs-compose-cli]
   * [Docker Compose Files][docker-docs-compose-file]

4. **IDEs**

   At the heart of good development is a good IDE (Integrated
   Development Environment). There is a lot of choice for both the API
   and SPA but the recommended IDEs are [IntelliJ IDEA][intellij-idea]
   and [Webstorm][intellij-webstorm] by JetBrains. Students are able to
   get their entire suite for free if you provide proof of registration.

   An alternative for developing the SPA with is Microsoft's [VS
   Code][vscode].

   It's also recommended that you install a database management tool, to
   help with any testing and to backup or restore data. Fortunately,
   JetBrains also make an IDE for this - [DataGrip][intellij-datagrip].

5. jq (a tool used for JSON processing)

   * On macOS, if you have [homebrew][homebrew] installed just run `brew
     install jq`
   * On Linux, it's likely `jq` is available from your package manager
   * If all else fails, you can [download it][jq]

## Getting started

To make getting started easier, and to help ensure everyone is following
the same processes, we have a ["development
repository"][development-repo] that contains everything you need to
know. To get started, navigate to somewhere on your computer (we
recommend setting a new folder up to keep everything organised) and run:

```sh
$ git clone git@github.com:backstage-technical-services/website-development.git development
```

The [included readme][development-readme] will contain any more
information on how to get the API and SPA downloaded and set up.

## Questions or need help?

If you have any questions or need help don't hesitate to ask in
[Slack][slack].

[contributing-main]: ../../Contributing.md
[contributing-workflow]: ./Development%20Workflow.md
[contributing-tools]: ../Our%20Tools.md
[install-sdkman]: https://sdkman.io/install
[install-nodejs]: https://nodejs.org/en/download
[install-yarn]: https://classic.yarnpkg.com/en/docs/install
[install-docker]: https://docs.docker.com/install
[install-docker-compose]: https://docs.docker.com/compose/install
[intellij-idea]: https://www.jetbrains.com/idea/download
[intellij-webstorm]: https://www.jetbrains.com/webstorm/download
[intellij-datagrip]: https://www.jetbrains.com/datagrip/download
[vscode]: https://code.visualstudio.com/download
[docker-compose-docs]: https://docs.docker.com/compose
[docker-container-exec]: https://docs.docker.com/engine/reference/commandline/container_exec
[docker-docs-compose-file]: https://docs.docker.com/compose/compose-file
[docker-docs-compose-cli]: https://docs.docker.com/compose/reference
[docker-docs]: https://docs.docker.com/engine/reference/commandline/cli
[docker-container-run]: https://docs.docker.com/engine/reference/commandline/container_run
[docker-images-vs-containers]: https://stackoverflow.com/a/23736802
[development-repo]: https://github.com/backstage-technical-services/website-development
[development-readme]: https://github.com/backstage-technical-services/website-development/blob/master/README.md
[slack]: https://bts-website.slack.com
[homebrew]: https://brew.sh
[jq]: https://stedolan.github.io/jq

