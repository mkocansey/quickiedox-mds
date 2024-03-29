# How QuickieDox Works

QuickieDox is a **purely vanilla PHP** project that leverages the following libraries to display markdown files documentation.


| Library                                                                              | URL                                                                                                         |
|:-------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------|
| [CommonMark](https://commonmark.thephpleague.com)                                    | Parses markdown files to be rendered as HTML.                                          |
| [TailwindCSS](https://tailwindcss.com)                                               | Nicely design and layout the documentation pages.                                               |
| [Prism JS](http://prismjs.com)                                                       | For syntax highlighting of code blocks.                                                  |
| [Guzzle HTTP Client](https://docs.guzzlephp.org/en/stable/overview.html) {nowrap="nowrap"} | Used for making  HTTP requests if testing is enabled. |


The [Installation](installation) steps simplifies how to get up and running with QuickieDox.

## So, What Is Really Happening Here?

Below is a high level breakdown of what happens when you access the documentation website you just cloned.

### First
The `index.php`{.inline} file at the root of the project handles vendor autoloading and setting of global variables defined in the `.env`{.inline} and `config.php`{.inline} files. The `routes.php`{.inline} file is then loaded and current url passed to the `Router`{.inline} class to serve content for the matching url. 

### Secondly
The `DocController.php`{.inline} file then decides what content to serve. The constructor in the `DocController`{.inline} class sets values for the page to be parsed and returned. This will either be the documentation page the user requested (by clicking on a link in the [navigation](convention-nav)) or the default page defined in the `config.php`{.inline} file. Where a page was specified but a corresponding `.md`{.inline} file was not found, a default `404.md`{.inline} is set as the page to parse and return.

Below are really the only types of content expected by the controller:

* The documentation home page.
* A 404 page for undefined routes.
* The default documentation page. This is sort of the first page you want to display anytime a user lands on your docs page. This is usually an `overview`{.inline} page or `installation`{.inline} page. Completely up to you.
* Any other documentation page defined in your `navigation.md`{.inline} file. A default `404.md`{.inline} page is displayed if no `.md`{.inline} file was found for the link clicked on.

### Thirdly
The DocController then hands off the file to be parsed to the `Doc`{.inline} class defined in `Core/Doc.php`{.inline}. Parsing is handled by [`league/commonmark`{.inline}](https://commonmark.thephpleague.com) and the resulting HTML is returned to the controller, where rendering is handed off to `views/reader.php`{.inline}.

### Lastly
At the view level, Javascript is then used to: 

* Set the page title to the `default_page_title`{.inline} defined in the config file plus what was defined in the first \<h1\> tag of the documentation page being viewed. Example: the title for this page is set to QuickieDox Documentation: How QuickieDox Works. *QuickieDox Documentation* is what has been defined in the config.php file for `default_page_title`{.inline}. *How QuickieDox Works* is what has been defined as the first \<h1\> on this page.
* Highlight the current page in the navigation so users knows what page they are viewing.
* Make navigation items collapsible and expandable. No two top level sections can be open at the same time.
* Draw the sub navigation within the documentation.
* Make all external links open in a new window/tab.
* Set the page theme (dark or light).
* Trigger the search box shortcuts.

{.alert.tip}
You are encouraged to just snoop around the code to better understand how documentation content is served. It is not complex at all.

&nbsp;