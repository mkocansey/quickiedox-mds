# How QuickieDox Works

QuickieDox is a **purely vanilla PHP** project that leverages the following libraries to display documentation.


| Library                                                                              | URL                                                                                                         |
|:-------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------|
| [CommonMark](https://commonmark.thephpleague.com)                                    | Used by QuickieDox to parse markdown files to be rendered as HTML.                                          |
| [TailwindCSS](https://tailwindcss.com)                                               | Used by QuickieDox to nicely spice up the documentatin pages.                                               |
| [Prism JS](http://prismjs.com)                                                       | Used by QuickieDox for syntax highlighting of code blocks.                                                  |
| [Animate.CSS](https://animate.style)                                                 | Used by QuickieDox to animate navigation items when expanded or collapsed.                               |
| [Symfony HTTP Client](https://symfony.com/doc/current/http_client.html#installation) | Used by QuickieDox when running endpoints for users who enable API endpoint testing in their documentation. |


In very simple steps, this is how QuickieDox works.

## 1. Clone the QuickieDox Repo

The first step is to clone the repo since this is not a composer package. 

### via HTTPS
```bash
# create a directory where you want to clone quickiedox
# cd into that directory and run 
```
{.command-line}
```bash
git clone https://github.com/mkocansey/quickiedox.git
```

### via SSH
```bash
# create a directory where you want to clone quickiedox
# cd into that directory and run 
```
{.command-line}
```bash
git clone git@github.com:mkocansey/quickiedox.git
```

## 2. Modify Configuration

You can either update the `config.php`{.inline} or the `.env`{.inline} file that is included with the project.  The `config.php`{.inline} file picks most of its configurations from the `.env`{.inline} so it is enough to change one of the files **not** both. It is however, advised to make changes in the `.env`{.inline} file to make it easy to replicate the project for another documentation.

## 3. Pull In The Markdown Files


The markdown files that make up the documentation are expected to sit in a directory you specify. The default is `markdown`{.inline}. The [assumption/convention]({version}/conventions) here is that your markdown files are hosted in their own git repo. There are three ways to pull in the markdown files.

### Just Copy and Paste

All QuickieDox needs to are `.md`{.inline} files in the `markdown`{.inline} directory. You can simple copy and paste your `.md`{.inline} files into this directory and voila! If your documentation is in versions, you will need to have a separate directory for every version number. For example, if your documentation has version 1.x and 2.x, you will need to create a `1.x`{.inline} and `2.x`{.inline} directories in the `markdown`{.inline} directory. You will then need to copy the appropriate `.md`{.inline} files into their respective directories. 
See the [Conventions > Versioning docs]({version}/convention-versions) for more on this.

### Go to This URL

It is possible to pull in your markdown files by visiting one of the routes defined in the project. Go to the root of the project you cloned and start the inbuilt PHP server using the command below:

{.command-line}
```bash
php -S localhost:8000
```

Once the server is started visit [http://localhost:8000/get-markdown](http://localhost:8000/get-markdown)


### Run This Bash Script

At the root of the project is a `get-markdown.sh`{.inline} shell script containing very few lines of code to clone the repo containing the markdown files. You will need to modify the script and put in the url to your markdown files repo. Next run the script as shown below in a terminal. You need to be at the root of your project.

{.command-line}
```bash
./get-markdown.sh
```

Once the markdown files are pulled in you can continue to browse the documentation [`https://localhost:80000`{.inline}](https://localhost:80000)


## So, What Is Really Happening Here?

Below is a high level breakdown of what happens when you access the documentation website you just cloned.

### First
The `index.php`{.inline} file at the root of the project handles vendor autoloading and setting of global variables defined in the `.env`{.inline} and `config.php`{.inline} files. The `routes.php`{.inline} file is then loaded and current url passed to the `Router`{.inline} class to serve content for the matching url. 

### Next
The `DocController.php`{.inline} file then decides what content to serve. The constructor in the `DocController`{.inline} sets values for the page to be parsed and returned. This will either be the page the user requested for or the default page defined in the config file. Where a page was specified but a corresponding `.md`{.inline} file was not found, a default `404.md`{.inline} is set as the page to parse and return.
There are really only three types of content expected by the controller:
* The docs home page
* The default documentation page. This is sort of the first page you want to display anytime a user lands on your docs page. This is usually an `overview`{.inline} page or `installation`{.inline} page. Completely up to you.
* Any other documentation page defined in your `navigation.md`{.inline} file. A default `404.md`{.inline} page is displayed if no `.md`{.inline} file was found for the link clicked on.

### Next
The DocController then hands off the file to be parsed to the `Doc`{.inline} class defined in `Core/Doc.php`{.inline}. Parsing is handled by `league/commonmark`{.inline} and the resulting HTML is returned to the controller, where rendering is handed off to `views/reader.php`{.inline}.

### Next
At the view level, Javascript is then used to: 
* Set the page title to the default defined in the config file plus what was defined in the first \<h1\> tag.
* Highlight the current page in the navigation so user knows what page they are viewing.
* Make navigation items collapsible and expandable.

{.alert.tip}
You are encouraged to just snoop around the code to better understand what how the documentation is served. It is not as complex as one might presume.

&nbsp;