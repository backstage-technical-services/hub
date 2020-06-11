# Development Workflow
To ensure consistency throughout the team, and to minimise the risk of releasing broken code, this project uses a set of 
pre-defined workflows that all team members must use. 

This project uses the Kanban system; all tickets must go through the stages sequentially, and each stage has a set of 
criteria that the ticket must meet before it is allowed to enter that stage. No one should work on something that is not 
a ticket on GitHub, no matter how small - this helps us track what everyone's currently working on and avoids conflicts.

If you are intending on working on the site, please make sure you are
familiar with this page.

# Ticket Stages

1. **Backlog:**

   All tickets begin their life in the "Backlog". This isn't a physical space and there isn't a label for it; this is 
   simply for tickets which we haven't agreed are ready to be worked on yet. These tickets will appear in the `Open` 
   column on the board. 

2. **Ready:** `status/ready`

   Once we have enough information to know how to implement a ticket and have agreed it should be worked on, it will be 
   marked as "Ready". Tickets should only be moved here by a Maintainer, as they'll know what means a ticket is ready to 
   be worked on.
   
3. **In Progress:** `status/in-progress`

   When you start working on a ticket (see below), mark it as "In Progress" and assign yourself to it (so everyone knows 
   who's working on it).

   > Don't want to work on a ticket anymore? Simply un-assign yourself and mark it as "Ready" again so that someone else 
   > can pick it up.

4. **Code Review:** `status/code-review`

   Once a ticket is complete and is ready to be released it needs to undergo a quick code review. This stage is performed 
   by another member of the team and is there simply to check that what you've done makes sense, and follows good 
   programming practices.

    > There's no need to change the assignee of the ticket to reflect the person performing the code review - this will 
    > be handled by the assignee of the merge request

5. **QA:** `status/qa`

   Once a ticket has passed code review and has deployed to our staging environment, it is ready for QA. This stage 
   verifies that the work functions as expected, resolves the ticket and doesn't adversely affect the rest of the site.

6. **Ready for Release:** `status/ready-for-release`

   Once a ticket passes QA, it is marked as "Ready for release". Only when all tickets in that release are in this stage 
   will the release be cleared to proceed.

Once a ticket is complete and released it will be automatically closed, and moved to the `Done` column in the board.

# Workflow

## Beginning work
When you pick a ticket and mark it as "In Progress", you can start working on it locally.

All work should be performed on its own branch, based on `master`. The name of this branch should be all lowercase, use 
hypens instead of spaces and include the ticket number and a short summary in the following format:

```
{number}-{short-summary}
```

## Committing your work
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

## Releasing your work
_This process can only be performed by a maintainer._

Once work is complete on a ticket, it can be released using a "release branch"; this branch is created from `master` and 
is named according to the following format:

```
release/{version}
```

A ticket is added to this release by creating a [merge request][pr-new] (MR) into this release branch, triggering the
code review process (this is when you move the ticket to `status: code-review`). You need to use the `Feature` MR 
template when writing this MR - this makes sure that those reviewing the MR know what's being merged. It's also 
important to make sure you reference the original ticket to make sure it's automatically closed when the work is merged 
into `master` at the end - see [this guide][pr-autoclose-tickets].

If the reviewer requests changes, you can simply push them to the original branch and they'll be picked up by the MR - 
no need to open a new one! Once all the discussions are resolved (or if there weren't any to start with), the MR can be 
approved. This will merge that branch into the release branch, and deploy the work to our staging environment.

Once the work has deployed to our staging environment, the ticket enters the QA stage (move the ticket to `status: qa`). 
If changes are requested they should also be pushed to the original branch, but these will need to be merged into the 
release branch with another MR - this makes sure that the changes also undergo a code review. Once the ticket passes QA 
it's ready to be released and can be moved to `status: ready-to-release`.

Once all of the tickets assigned to that release are ready, the entire release branch is merged into `master`. This can 
be performed using an MR (although this merge request doesn't need to be approved) but it's often easier to perform this 
merge locally and push. 

The release is performed by tagging the release commit with a version tag: `{version}` (this should be the same as the
`release/{version}` branch name). The tag's release notes should include a list of everything being released (use the
previous MRs to help you), linking back to the original ticket where possible.

> We haven't set up CI/CD to automatically deploy code changes since
> moving back to GitHub, so any updates need to be manually done. Ask in
> Slack for help.

## Tidying Up
Once a release has been deployed, there are a few bits of housekeeping to do:

* Make sure all of the tickets in the release have been closed automatically. If they haven't, manually close them with 
  a comment that links to the release.
* Delete all the branches that were in the release
* Close the milestone (if applicable)

[atomic-commits]: http://www.pauline-vos.nl/atomic-commits/
[commit-message-guide]: https://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html
[pr-new]: https://github.com/backstage-technical-services/laravel-site/compare
[pr-autoclose-tickets]: https://help.github.com/en/github/managing-your-work-on-github/linking-a-pull-request-to-an-issue
