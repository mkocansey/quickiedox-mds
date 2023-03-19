# Contribution Guide 

QuickieDox's [known issues](known-issues) page keeps track of issues that can potentially be worked on by contributors. This list is not extensive. Users are encouraged to report other issues on our [GitHub page](https://github.com/mkocansey/quickiedox/issues).

## Bug Reports & Questions

To help us keep all bug reports and questions consolidated and also to serve as a reference for others who might have the same questions or reports, we encourage you to use post all questions and bug reports on our GitHub issues page.

## Branching && Pull Requests

Before working on a feature or issue, we encourage you to take a look at our [GitHub issues page](https://github.com/mkocansey/quickiedox/issues) to ensure you are not working on something already in progress or that has already been closed and probably awaiting a merge into main. Every issue or feature being worked on will have an assignee. Any issue without an assignee can be picked up and worked on by anyone. 

To work on an issue that is not listed, kindly create the issue on our [GitHub issues page](https://github.com/mkocansey/quickiedox/issues) and assign to yourself. 

Every issue or feature being worked on must be in its own branch with the branch name being the issue number prefixed with quickie. For example: if you decide to work on issue #13, your branch name should be `quickie-13`{.inline}.

{.alert.note}
All branching must be from the `main`{.inline} branch. All pull requests should be into the `main`{.inline} branch.



## Compiled Assets

The only compiled asset in the QuickieDox codebase is the `assets > css > quickiedox.css`{.inline} file which takes it source from `src > index.css`{.inline}. We encourage contributors to make changes to the source css file but not submit a compiled css file. This makes it easier to review what has been addded as css.


## Coding Style 



## Code of Conduct

QUickieDox derives its code of conduct from [The Ruby Community Conduct Guideline](https://www.ruby-lang.org/en/conduct/) and we advise contributors to be respectful of these.

* Participants will be tolerant of opposing views.
* Participants must ensure that their language and actions are free of personal attacks and disparaging personal remarks.
* When interpreting the words and actions of others, participants should always assume good intentions.
* Behaviour which can be reasonably considered harassment will not be tolerated.