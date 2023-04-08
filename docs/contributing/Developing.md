# Contributing - Developing

> Please make sure you have read the [main contribution guide][contributing-main] first and are familiar with
> the [development workflow][contributing-workflow].
>
> It would also be a good idea to familiarise yourself with [our tools][contributing-tools].

## Pre-requisites

Before you start developing, please make sure you have the following set up on your computer.

> **Note:** While it is possible to use all of these tools and work on the website on Windows, it is strongly
> recommended that you use a Linux VM or the Windows Subsystem for Linux in order to take advantage of the tooling we
> use to simplify some processes.

### Docker and Docker Compose

In order to run any auxiliary services (eg, the SMTP server and database) you will need to
have [Docker installed][install-docker], as well as [Docker Compose][install-docker-compose].

It's recommended you are familiar with the following:

- [Images and containers][docker-images-vs-containers]
- [Running containers][docker-container-run]
- [Executing commands in containers][docker-container-exec]
- [Docker compose][docker-compose-docs]

If you want to learn more, Docker's documentation is fantastic:

- [Docker][docker-docs]
- [Docker Compose CLI][docker-docs-compose-cli]
- [Docker Compose Files][docker-docs-compose-file]

### IDEs

At the heart of good development is a good IDE (Integrated Development Environment). There is but the recommended IDEs
are [IntelliJ IDEA][intellij-idea] and [Webstorm][intellij-webstorm] by JetBrains. Students are able to get their entire
suite for free if you provide proof of registration.

An alternative for developing the SPA with is Microsoft's [VS Code][vscode].

It's also recommended that you install a database management tool, to help with any testing and to back-up or restore
data. Fortunately, JetBrains also make an IDE for this - [DataGrip][intellij-datagrip].

### SSH Key

You can follow [this guide][ssh-create] to create an SSH key if you do not already have one,
and [this guide][ssh-github] to add it to your GitHub account.

### GPG Key

- Follow [this guide][gpg-create] to create a new GPG key. Make sure it is RSA 4096.
- Follow [this guide][gpg-github] to add it to GitHub
- You can sign a commit by using the `-S` flag
- You can configure git sign all commits for the current repository with

  ```sh
  $ git config commit.gpgsign true 
  ```
- You can configure git to sign all commits for all repositories with

  ```sh
  $ git config --global commit.gpgsign true
  ```

## Getting started

To get started, simply follow the readme of the website:

- [v4 Website](https://github.com/backstage-technical-services/website/blob/main/readme.md#installing)

## Questions or need help?

If you have any questions or need help don't hesitate to ask in [Slack][slack].

[contributing-main]: ../../Contributing.md
[contributing-workflow]: ./Development%20Workflow.md
[contributing-tools]: ../Our%20Tools.md
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
[slack]: https://bts-website.slack.com
[homebrew]: https://brew.sh
[ssh-create]: https://docs.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent
[ssh-github]: https://docs.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account
[gpg-create]: https://docs.github.com/en/github/authenticating-to-github/generating-a-new-gpg-key
[gpg-github]: https://docs.github.com/en/github/authenticating-to-github/adding-a-new-gpg-key-to-your-github-account

