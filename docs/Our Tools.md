# Our Tools

We use a variety of tools to help with the development of the site, as
well as automation of common tasks.

Most of these tools are free to use by anyone; if you would like access
you can ask someone in [Slack][slack].

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
* `ops-security`: This is where we talk about anything security related.
  [Snyk](#snyk) also posts notifications of vulnerabilities here.
* `service-github`: This is where important notifications from GitHub
  are posted, including new Pull Requests.
* `service-rss`: This is where any potentially interesting news in the
  world of tech is posted.

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

### Integrations

Our Slack workspace has a few integrations installed to make everyone's
lives slightly easier:

* **GitHub:** This allows you to interact with GitHub issues and PRs
  without needing to go to the website! It also posts notifications to
  the `service-github` channel.
* **Google Drive:** This allows you to see previews of files and folders
  within Slack when a link is posted (as long as you have access to it).
  You can even find and create files right from within Slack.
* **Google Hangouts:** We use Google Meet (aka Hangouts) for our
  meetings; using this integration you can create a meet from within
  Slack.
* **Giphy:** For those times when an animated GIF perfectly sums up your
  reaction to something.
* **Bugsnag:** Bugsnag is the application that monitors v4 of the
  website, and instantly reports in Slack when an error occurs so that
  we know that a problem's occurred even before the user can report the
  issue in GitHub.

  > This integration is being deprecated as it is not supported by
  > Quarkus. v5 of the website will use Sentry.io instead.

As we are on the free plan we can only add a limited number of
integrations, however if there's something that you think would be
useful then let the Slack Admins know!

## Git

All parts of the website use git for version control and to make
collaboration between multiple team members easy.

If you are unfamiliar with git, GitHub have a [handbook][git-handbook]
on basic git usage.

## GitHub

[GitHub][github] houses all our source code and [issue
tracker][github-issues], which is where people can report bugs and
request features.

Some of our repositories also make use of GitHub Actions to run our
CI/CD workflows, which are used to automate the build and deployment of
that software.

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

See the [Use of Labels][label-usage] document.

### Milestones

We sometimes use milestones to group issues that we want to release
together, and track the progress of upcoming releases. Only issues
should ever be assigned to milestones, to avoid duplicating information
on the milestone.

## ZenHub

While GitHub's issue tracker is very powerful, it can be difficult to
see at a glance how everything is progressing. GitHub Projects offers
promise for a fully integrated solution, but until it is more mature we
use [ZenHub][zenhub-board].

This is a Kanban board (where issues are brought in and worked on
whenever they're ready), and allows us to easily see and manage issues.
This board is the recommended way to manage lots of issues in one go, or
to easily see what tickets you can start working on.

You can see this board from within GitHub if you [install the
extension][zenhub-extension]. This adds an additional tab to the
[hub][github-issues] alongside Issues and Pull Requests.

Anyone in the GitHub organisation will be able to see this board,
although you may need to authorise the app and log in with GitHub first.

See the [Development Workflow][contributing-workflow] for information on
what the different columns mean.

## CircleCI

GitHub Actions is sadly a little limited for some of the complex CI/CD
workflows needed by the API and SPA. Until it has matured, these two
repositories use [CircleCI][circleci], a leader in the world of CI/CD.

As our repositories are Open-Source Software (OSS), CircleCI grants us a
very large number of credits to use for builds. However, some builds can
take a long time so we only trigger them for Pull Requests and commits
on `master`. As a result, you should only open a Pull Request when the
work is ready to be reviewed.

Sensitive information, such as API tokens and auth credentials, are
injected into each job using environment variables. We also take
advantage of a feature called "Contexts" to allow us to re-use these
sensitive values across both repositories.

Anyone in the GitHub organisation can access the CircleCI builds; just
ensure you log in with GitHub and select the
`backstage-technical-services` organisation and then the repository you
want to view.

## SonarCloud

[SonarCloud][sonarcloud] is a code quality analysis code that can be
used to ensure all of your code is clean, and can even detect bugs and
"code smells" (code that is indicative of logic errors that may lead to
bugs in future).

SonarCloud is a required CI step for all Pull Requests and builds on
`master`, with some checks that have to pass in order for the code to be
considered healthy:

* Test coverage > 70%
* High maintainability
* High reliability
* Minimal duplicated lines (< 3%)

SonarCloud will even post the results of the check as a comment in Pull
Requests, but you can also view the results of any branch or Pull
Request in the [dashboard][sonarcloud].

Anyone in the GitHub organisation can access SonarCloud; just log in
with your GitHub account.

## Snyk

All projects need to use third-party dependencies as the last thing you
want to do is re-invent the wheel for everything. Sadly, with this comes
the risk that these dependencies contain a vulnerability that can be
exploited.

[Snyk][snyk] automatically analyses our dependencies to detect these
vulnerabilities, and informs us when one is found. It's both a required
step in our CI process (so new dependencies don't introduce
vulnerabilities), but it also continually monitors our apps and notifies
us of any new vulnerabilities. It even creates Pull Requests
automatically to resolve the issues, if it can.

Sadly Snyk.io is not linked to the GitHub organisation, so access is
limited. However, you can request access by asking in Slack.

## Sentry

Sentry is a cloud-based error monitoring tool used to detect application
errors in real-time, allowing you to react to issues without needing
users to report bugs in GitHub.

We haven't yet set up Sentry, but it will be integrated into the API.

## One-Time Secret

[One-Time Secret][onetimesecret] is used to share sensitive information,
such as environment files. This tools gives you a link that can only be
used once for you to give to the recipient. For additional security, you
can also set a timeout on the link and provide a passphrase to ensure
the person using the link is the intended recipient.

You do not need an account to use this tool.

[slack]: https://bts-website.slack.com
[git-handbook]: https://guides.github.com/introduction/git-handbook/
[github]: https://github.com/backstage-technical-services
[github-register]: https://github.com/join
[github-issues]: https://github.com/backstage-technical-services/hub/issues
[github-team]: https://github.com/orgs/backstage-technical-services/people
[label-usage]: ../Use%20of%20Labels.md
[zenhub-board]: https://app.zenhub.com/workspaces/website-5ee3b9f45f28495afe8be3f9/board
[zenhub-extension]: https://www.zenhub.com/extension
[circleci]: https://app.circleci.com/projects
[sonarcloud]: https://sonarcloud.io/projects
[snyk]: https://app.snyk.io/org/backstage-technical-services/projects
[contributing-issues]: ./contributing/Reporting%20Issues.md
[contributing-developing]: ./contributing/Developing.md
[contributing-workflow]: ./contributing/Development%20Workflow.md
[onetimesecret]: https://onetimesecret.com

