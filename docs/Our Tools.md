# Our Tools

We use a variety of tools to help with the development of the site, as well as automation of common tasks.

Most of these tools are free to use by anyone; if you would like access you can ask someone in [Discord](#discord   ).

## Discord

Good communication is vital and ours happens on the society's Discord server; this is also our primary method of
interacting with the wider society.

We don't want anyone to be left out so all discussions must happen here, no matter how big or small - please don't use
external social media apps like Facebook, or even emails.

Discord is also the place where you can request access to any of the other tools listed in this document.

Discord is open to everyone; you can get access by [asking the Secretary][secretary].

### Channels

We make use of channels to group conversations with a similar subject. It's important that conversations are kept to the
relevant channel to prevent others being "spammed" with things they may not be interested in and make it easier to find
conversations at a later date.

The channels that everyone can see and interact with:

- `website-announcements`: This is for the web dev team to announce new features, or major changes to the website, to
  the wider society
- `website-feedback`: This is for society members to provide feedback (reporting bugs, requesting features, etc) without
  needing to create an issue in GitHub
- `website-preview`: This is somewhere the web dev team can provide "sneak peeks" at upcoming changes, and potentially
  get early feedback

The channels that only those in the web dev team can access:

- `website-general`: This is for any general internal conversation that doesn't have a dedicated channel
- `github-notifications`: This is where we receive notifications about changes to GitHub (eg, new issues, new Pull
  Requests, etc)
- `bugsnag`: This is where BugSnag reports errors that occur in production
- `website-hosting`: This is where we talk about the hosting provider

We also have a voice channel (`webdev`) for any meetings.

## Git

All parts of the website use git for version control and to make collaboration between multiple team members easy.

If you are unfamiliar with git, GitHub have a [handbook][git-handbook] on basic git usage.

## GitHub

[GitHub][github] houses all our source code and [issue tracker][github-issues], which is where people can report bugs
and request features.

Some of our repositories also make use of GitHub Actions to run our CI/CD workflows, which are used to automate the
build and deployment of that software.

Anyone with a [GitHub account][github-register] is able to create issues, and members can request access to
the [GitHub organisation][github-team] if they wish to work on the website. See [Reporting Issues][contributing-issues]
and [Developing][contributing-developing] respectively.

If you want to develop on the site, make sure you have [set up an SSH key][github-ssh]
and [sign your commits][github-sign].

### Use of labels

See [this document][label-usage] on how we use labels to categorise and group issues.

### Milestones

We sometimes use milestones to group issues that we want to release together, and track the progress of upcoming
releases. Only issues should ever be assigned to milestones, to avoid duplicating information on the milestone.

## SonarCloud

[SonarCloud][sonarcloud] is a code quality analysis tool used by some repositories that can be used to ensure all of
your code is clean, and can even detect bugs and "code smells" (code that is indicative of logic errors that may lead to
bugs in future).

SonarCloud is a required CI step for all Pull Requests and builds on `main`, with some checks that have to pass in order
for the code to be considered healthy:

- Test coverage > 70%
- High maintainability
- High reliability
- Minimal duplicated lines (< 3%)

SonarCloud will even post the results of the check as a comment in Pull Requests, but you can also view the results of
any branch or Pull Request in the [dashboard][sonarcloud].

Anyone in the GitHub organisation can access SonarCloud; just log in with your GitHub account.

## Bugsnag

Bugsnag is a tool that we use to report any errors in production to Discord; this provides valuable additional detail
around the error (eg, any database queries, internal logs, the stacktrace, etc) that makes identifying the cause much
easier.

## One-Time Secret

[One-Time Secret][onetimesecret] is used to share sensitive information, such as environment files. This tools gives you
a link that can only be used once for you to give to the recipient. For additional security, you can also set a timeout
on the link and provide a passphrase to ensure the person using the link is the intended recipient.

You do not need an account to use this tool.

## Google Drive

We use [Google Drive][gdrive] for general admin, planning and storing documents, such as logos for the website. Anyone
in the team can ask for access to the folder, and it is available to all committee members.

[secretary]: mailto:sec@bts-crew.com?subject=Slack%20access
[git-handbook]: https://guides.github.com/introduction/git-handbook/
[github]: https://github.com/backstage-technical-services
[github-register]: https://github.com/join
[github-issues]: https://github.com/backstage-technical-services/hub/issues
[github-team]: https://github.com/orgs/backstage-technical-services/people
[github-ssh]: https://help.github.com/en/enterprise/2.17/user/github/authenticating-to-github/connecting-to-github-with-ssh
[github-sign]: https://help.github.com/en/github/authenticating-to-github/signing-commits
[label-usage]: ../Use%20of%20Labels.md
[sonarcloud]: https://sonarcloud.io/projects
[contributing-issues]: ./contributing/Reporting%20Issues.md
[contributing-developing]: ./contributing/Developing.md
[contributing-workflow]: ./contributing/Development%20Workflow.md
[onetimesecret]: https://onetimesecret.com
[gdrive]: https://drive.google.com/drive/folders/1YejLL2mTgzXfKU96bambQ6f3N1pLz9MQ

