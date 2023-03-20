# Contribution Guide 

QuickieDox's [known issues](known-issues) page keeps track of issues that can potentially be worked on by contributors. This list is not extensive. Users are encouraged to report other issues on our [GitHub page](https://github.com/mkocansey/quickiedox/issues).

## Bug Reports and Questions

To help us keep all bug reports and questions consolidated and also to serve as a reference for others who might have the same questions or reports, we encourage you to use post all questions and bug reports on our GitHub issues page. Bug reports should be descriptive enough to be reproducable. It is good practice to include the following in your bug report.

* QuickieDox version number
* PHP version
* OS
* Web server (Apache, NGINX, etc)
* Browser type and version

[This article](https://opensource.guide/how-to-contribute/#how-to-submit-a-contribution) has good general guidelines on how to submit a contribution.


## Pull Requests and Branching

Before working on a feature or issue, we encourage you to take a look at our [GitHub issues page](https://github.com/mkocansey/quickiedox/issues) to ensure you are not planning to work on something already in progress or has already been closed and probably awaiting a merge into `main`{.inline}. Every issue or feature being worked on will have an assignee. Any issue without an assignee can be picked up and worked on by anyone. 

To work on an issue that is not listed, kindly create the issue on our [GitHub issues page](https://github.com/mkocansey/quickiedox/issues) and assign to yourself. 

For changes that address core functionality or would require breaking changes (e.g. a major release), it is best to [open an Issue](https://github.com/mkocansey/quickiedox/issues) to discuss your proposal first. This is not a must but can save time creating and reviewing changes down the line.

In general, QuickieDox follows the "[fork-and-pull](https://github.com/susam/gitpr)" Git workflow

* Fork the repository to your own Github account.
* Clone the project to your machine.
* Create a branch locally with a `quickie`{.inline} prefix followed by issue number.
* Commit changes to the branch following the formatting guidelines specific to this repo.
* Push changes to your fork.
* Open a PR in our repository.

{.alert.stop}
Every issue or feature to be worked on must be in its own branch with the branch name being the issue number prefixed with quickie. For example: if you decide to work on issue #13, your branch name should be `quickie-13`{.inline}.


## Compiled Assets

The only compiled asset in the QuickieDox codebase is the `assets > css > quickiedox.css`{.inline} file which takes it source from `src > index.css`{.inline}. We encourage contributors to make changes to the source css file but not submit a compiled css file. This makes it easier to review what has been addded as css.


## Coding Style 

QuickieDox adheres to the [PSR-2](https://www.php-fig.org/psr/psr-2/) coding standards as well as the [PSR-4](https://www.php-fig.org/psr/psr-4) autoloading standards. 

Your methods will need to have adequate PHPDoc documentation blocks as shown below. Note how parameters have explicitly defined types and methods also have explicit return types.

```php
/**
 * Remove .md extension from file
 * @param string $page
 * @return string
 */
public static function stripMdExtension(string $page): string
{
    // code here
}
```



## Code of Conduct

QUickieDox derives its code of conduct from [The Ruby Community Conduct Guideline](https://www.ruby-lang.org/en/conduct/) and we advise contributors to be respectful of these.

* Participants will be tolerant of opposing views.
* Participants must ensure that their language and actions are free of personal attacks and disparaging personal remarks.
* When interpreting the words and actions of others, participants should always assume good intentions.
* Behaviour which can be reasonably considered harassment will not be tolerated.