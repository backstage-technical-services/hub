# Our Tools

We use a variety of tools to help with the development of the site, as
well as automation of common tasks.

Most of these tools are free to use by anyone; if you would like access
you can ask someone in [Slack][slack].

## Git

All parts of the website use git for version control and to make
collaboration between multiple team members easy.

GitHub have made a handy [handbook][git-handbook] on basic git usage.

## GitHub

[GitHub][github] houses all our source code and [issue
tracker][github-issues], which is where people can report bugs and
request features.

Some of our repositories also make use of GitHub Actions to run our
CI/CD workflows, which are used to automate the build and deployment of
that software. Due to some limitations with GitHub, some of our
repositories use [CircleCI](#circleci) instead.

Anyone with a [GitHub account][github-register] is able to create
issues, and members can request access to the [GitHub
organisation][github-team] if they wish to work on the website. See
[Reporting Issues][contributing-issues] and
[Developing][contributing-developing] respectively.

### Tickets vs issues

Within the team, we refer to issues in the issue tracker as "tickets";
we feel this better explains what the issues represent (after all, not
all tickets are actually issues - they may be requests or even
questions).

### Use of labels

See the [Usage of Labels][label-usage] document.

### Milestones

Using milestones is optional, but they can be a useful way of tracking
upcoming releases and organising tickets into a specific release. Only
tickets should be assigned to a milestone.

## Slack

Good communication is vital and ours happens on [Slack][slack], a
popular communication platform designed specifically for developers.

We don't want anyone to be left out so all discussions must happen here,
no matter how big or small - please don't use external social media apps
like Facebook, or even emails.

Slack is also the place where you can request access to any of the other
tools listed in this document.

Slack is open to everyone; you can get access by asking the Secretary.

### Channels

Slack makes use of channels to group conversations with a similar
subject. It's important that conversations are kept to the relevant
channel to prevent other members being spammed with things they may not
be interested in.

By default all new members are added to the `#general` channel, which is
for any general conversations unrelated to any development. All channels
are open to everyone so you can join others simply by searching in the
top bar and clicking "Join Channel".

Some other potentially useful channels are:

* `general-dev`: This is where any general development-related
  conversations happen. This will include discussing any tickets that
  don't have their own channel.
* `ops-domain`: This is where we talk about the `bts-crew.com` domain;
  including the registry, renewals, TLS certificates etc.
* `ops-hosting`: This is where we talk about the hosting provider for
  the website.
* `service-github`: This is where important notifications from GitHub
  are posted, including new Pull Requests.
* `service-rss`: This is where any relevant news in the world of tech is
  posted.

### Notifications

Slack is very powerful when it comes to notifications - it allows you to
customise notifications for each channel, with separate rules for both
desktop and mobile.

The most common reason you might not know what's going on is if you have
notifications off, or set to `Just mentions`.

### Using mentions

You can mention people in a Slack message simply by including their
username after an `@` symbol (if you type `@` Slack will give you some
hints). Those with the correct permissions can also use `@here`,
`@channel` and `@everyone` if the post is really important so everyone
gets a notification.

### Apps

_Needs detail_

## CircleCI

_Needs detail_

## SonarCloud

_Needs detail_

## Snyk

_Needs detail_

## Sentry

_Needs detail_

## One-Time Secret

[One-Time Secret][onetimesecret] is used to share sensitive information,
such as environment files. You do not need an account to use this tool.

[git-handbook]: https://guides.github.com/introduction/git-handbook/
[github]: https://github.com/backstage-technical-services
[github-register]: https://github.com/join
[github-issues]: https://github.com/backstage-technical-services/hub/issues
[github-team]: https://github.com/orgs/backstage-technical-services/people
[label-usage]: ../Usage%20of%20Labels.md
[contributing-issues]: ./contributing/Reporting%20Issues.md
[contributing-developing]: ./contributing/Developing.md
[slack]: https://bts-website.slack.com
[onetimesecret]: https://onetimesecret.com
