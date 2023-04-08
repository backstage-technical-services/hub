# Development Workflow

To ensure consistency throughout the team, and to minimise the risk of releasing broken code, this project uses a
workflow that all tickets must follow.

We use a Kanban system to allow us to work on any ticket as soon we can, but all tickets must go through the stages
sequentially, and each stage has a set of criteria that the ticket must meet before it is allowed to enter that stage.
No one should work on something that is not a ticket on GitHub (no matter how small); this helps us track what
everyone's currently working on and avoids conflicts.

## Ticket Lifecycle

1. **Triage:** `status/triage`

   All new tickets must start with what's called "triage"; this is a process that someone must go through to determine
   what a ticket needs before it is ready to be worked on.

   This process is mostly driven by experience and so there is no hard-and-fast rule as to what "ready" means, but the
   reviewer will read the ticket description and determine what further information is needed (called "refinement")
   before it can be worked on by a developer. This could include:

   * UI designs
   * Planning the domain/database structure
   * Researching possible solutions
   * Gaining community feedback

   The reviewer will add a series of labels with the `needs` prefix to indicate what information is needed. Triage is
   complete once the `status/triage` label is removed, and it moves to the "Refinement" stage.

   > A ticket may not need refinement if this triage process determines it to be sufficiently detailed; in which case it
   > can progress straight to `Ready`.

2. **Refinement**

   Once a ticket has been triaged it must be refined; this is a fancy word for resolving all of the `needs` labels. Each
   label must be either resolved or deemed no longer necessary (however, you should check with the person who triaged
   the ticket first). As each label is removed, the results of the refinement must be added to the ticket, either as a
   comment or in the description.

   Once all of the `needs` labels have been removed, the ticket can progress to the next stage.

3. **Ready:** `status/ready`

   Once we have enough information to know how to implement a ticket and have agreed it should be worked on, it will be
   marked as "Ready". This means a member of the development team can begin working on it whenever they want.

4. **In Progress:** `status/in-progress`

   When you start working on a ticket (see [below](#beginning-work)), mark it as "In Progress" and assign yourself to it
   so everyone knows who's working on it. It's important to communicate that you've picked up the ticket and are open to
   working on it with others, as someone else may be interested in working on it too.

   If at any point you can no longer continue with the ticket then mark is as "Ready", unassign yourself and post a
   comment of where you got to and why you had to stop. This is so that someone else can pick it up.

5. **Review:** `status/in-review`

   Once the work on a ticket is completed it goes through 2 stages of review:

   * **Code Review:** This is performed by other members of the team when a Pull Request is opened. This simply checks
     that what you've done makes sense and follows good programming practices. This step uses CI/CD pipelines to check
     common issues, such as tests and, vulnerabilities and code quality.
   * **Quality Assurance (QA):** This is performed after the Pull Request is approved and merged and simply verifies
     that the work does resolve the ticket without adversely affecting the rest of the site. For most tickets with a
     good coverage of tests, this is a very quick check to ensure that the new code deploys successfully.

6. **Released**

   Once a ticket passes QA it is ready to be released! Anyone with access to the CI/CD workflow can perform this process.

## Workflow

### Beginning work

When you pick a ticket and mark it as "In Progress", you can start working on it locally.

All work should be performed on its own branch, based on `main`. The name of this branch should be all lowercase, use
hypens instead of spaces and include the ticket number and a short summary of the work in the following format:

```
{number}-{short-summary}
```

### Committing your work

You should commit your work frequently, with each commit containing a small change. These are known as "atomic commits",
and make it easier to understand the commit history, as well as resolve conflicts and revert broken code.

Each commit message should begin with the ticket number and include a more detailed description if you feel you need
more than 50 characters to explain the work.

```
{#}: {commit summary}

{optional commit description}
```

See [this guide on atomic commits][atomic-commits] and [this one on good commit messages][commit-message-guide] for more
information.

> If your commits are getting rejected due to them being unsigned, you will need to [generate a GPG key][add-gpg-key]
> and [sign your commits][signed-commits]. We enforce signed commits to ensure those committing are who they say they
> are - see this [interesting post][why-sign-commits] for more information.

### Releasing your work

Your work is released to the world by merging it into the `main` branch using a Pull Request (PR).

#### Creating a Pull Request (PR)

Once the ticket is complete, ensure you have pushed it all and then navigate to the repository and
click `Pull requests > New pull request`. The `compare` branch should be your branch, and the `base` branch should
be `main`.

It is very important that when you make a PR you enter a descriptive title and detailed description. At the very least,
the title should include the ticket number and a brief summary of the work, but make sure this title doesn't go over the
character limit in GitHub.

Writing a good PR description is a skill in and of itself, but the important thing to remember is to describe why and
not what. Code should be self documenting and so what it's doing should be obvious to those reviewing, but what may not
be obvious is why you chose that approach. Use the PR to inform and justify any decisions (if anything this prevents
any "why did you do this?" comments), and highlight any issues you encountered - it's likely you learned something while
completing this work and PRs are a great way to distribute this knowledge to the rest of the team. Make sure you use the
PR template and have filled it in correctly.

> **Tip:** if your work isn't quite complete, but you want people to take a look at it early, you can open a draft PR.
> Once then work is complete, you can then mark this as "Ready for review".

Once you have opened a PR you should mark the ticket as "In Review".

#### Reviewing a Pull Request

Reviewing a PR should be a constructive process, and a learning opportunity for both the author and reviewers. Any
comments you leave, as well as replies to other comments, must be constructive. If you feel strongly about a comment, it
is often a good idea to chat to the other party directly in Slack (either by text or call) and don't be afraid to use
someone else as a mediator!

If the reviewer has requested changes you can simply commit and push them to the same branch and they'll be picked up by
the PR. If you do, any existing reviews will be marked as "stale" so you'll need to re-request any reviews.

#### Merging the Pull Request

Once a PR is approved and all the CI/CD checks have passed you can merge the PR simply by pressing the "Squash and
merge" button.

> **Tip:** GitHub scans the contents of commits merged into `main` and if the commit contains
> a [recognised keyword][pr-autoclose-tickets] GitHub will automatically close the ticket for you.

When merging, make sure you use a reasonable commit title and message. The PR title is often sufficient for the commit
title, but it is often a good idea to include any details in the PR description in the commit message to help anyone
looking at the git history understand what's going on.

> We enforce squashing and merging for all repositories to prevent `main` from containing any merge commits, as this
> makes it hard to understand the history, and ensure that it is linear.

#### Quality Assurance

Once the PR has been merged the work will automatically build and deploy to our [staging environment][staging]. This
allows us to verify that the work deploys successfully and meets the requirements of the ticket.

#### Deploying to production

Once the ticket passes QA, it can be deployed to production by an authorised user. You can ask in Slack for help.

If this succeeds, congratulations - you've just deployed some code to the website!

### Tidying Up

Once your work has been deployed, there may be a few bits of housekeeping to do:

* Make sure the ticket has been closed. If it hasn't included a comment in the issue that links to the commit hash that
  closed the issue, and then manually close it
* Close any milestones, if applicable

[atomic-commits]: http://www.pauline-vos.nl/atomic-commits/
[commit-message-guide]: https://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html
[add-gpg-key]: https://help.github.com/en/github/authenticating-to-github/adding-a-new-gpg-key-to-your-github-account
[signed-commits]: https://help.github.com/en/github/authenticating-to-github/signing-commits
[why-sign-commits]: https://mikegerwitz.com/2012/05/a-git-horror-story-repository-integrity-with-signed-commits
[pr-autoclose-tickets]: https://help.github.com/en/github/managing-your-work-on-github/linking-a-pull-request-to-an-issue
[staging]: https://staging.bts-crew.com

