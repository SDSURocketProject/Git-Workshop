# GitLab Website Usage

Note about cloning from out GitLab instance:

Because of heavy restrictions on networking on our server put on us by SDSU ITSO, our Rocket.Chat instance
cannot coexist with the http availability of the GitLab instance. Due to this, the GitLab instance is only
available via https. Zack is negotiating with the school to make the GitLab instance available via ssh.

In order to clone a repo, you must use https. To do this, use the http clone url provided by the website,
then change the http at the beginning to https. That change will be kept, and will only need to be made
while cloning.

## Issues

Anyone can file an issue to a repo. An issue doesn't necessarily need to be an "issue," they are just used
to keep track of any bugs, feature requests, suggested changes, etc, that need to be addressed.

All issues, like all merge requests, have an associated number and name that can be used to refer to them.

Issues have four important fields besides the name and number:

### Description

It is extremely important to fully describe each issue. For bug reports, describe exactly what the bug is,
including what happened, when it happened, steps to reproduce, and any other relevant information that can be
used to diagnose the bug.

For feature requests, suggested changes, etc, be precise in exactly what you want changed, and to what.

### Assignees

You can assign individuals to an issue. Assign the people responsible for the code the issue is about,
or the section manager if it is radically new. The section manager can then assign people as they see fit.

### Labels

Labels can be applied to an issue to help describe it. Labels are useful because they can be used to filter
issues, and to get a general sense of an issue based on the title and label.
Some examples of labels include: "bug," "good first issue," "feature," and "help wanted."

### Milestones

Milestones are long-term goals that many issues and merge requests will work towards. Milestones could be
things like "Flight Ready," "Version 1.0.0," "Complete rework of system X," etc. Milestones will keep track
of the total number of associated issues and merge requests, to show a "percent complete" metric and can be
given a due date.

## Merge Requests

Merge requests are an official way of requesting one branch to be merged into another. This is the only way
to merge a branch into master, but should be used for all merges. Merge requests have the same four major
fields as an issue.

The description for a Merge Request should list all changes made in the merge as an itemized list, and a reference to
the issue the requests addresses (if any). The description of the merge request is a good place to go into more detail
about the changes than commit titles allow, without requiring the reviewers to individually view possibly hundreds
of commit messages to see details of all changes.

Once a merge request is created, all assignees must review the merge request. They can start discussions or
create issues to address any problems with the merge request. If the maintainers disapprove of the merge, they
can request changes or close the merge request. If all maintainers approve the merge request, then a maintainer
may complete the merge.

## CI/CD

CI/CD (Continuous Integration / Continuous Development) is a complex automated system for performing tests
on codebase changes. The tests are configurable via a file called `.gitlab-ci.yml` in the base directory of a
repo, and is too complex for this document.

More information about this system can be found at this url:

[gitlab-ci-cd](https://docs.gitlab.com/ee/ci/)
