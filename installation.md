# Installation

Quickly create elegant documentation from markdown files. That is QuickieDox. 

The idea is to keep this as light as possible so QuickieDox is a **purely vanilla PHP** project and should work with most versions of PHP though version 8 is what is locked in the composer file. See [customization]({version}/php-version) for how to change this. 

QuickieDox was inspired a lot by the [Laravel documentation](https://laravel.com/docs). Being a regular user of the Laravel docs website, it was intriguing to learn they loaded the docs from [markdown files](https://github.com/laravel/docs). I snooped around the repo a bit and that gave rise to this project.

## The Ideal Use Case

You have a project that requires you to write out some documentation for either yourself or others to read. This may necessarily not be a technical project, anything that requires documentation is ideal. QuickieDox gives you a headstart with an already beautifully designed documentation website that only requires your markdown files to work its magic.

## Clone the Repo

There is nothing to composer install here. To create your own documentation website, just clone the repo and head over to [customization]({version}/homepage). 

### via HTTPS
```bash
// create a directory where you want to clone quickiedox
// cd into that directory and run 

git clone https://github.com/mkocansey/quickiedox.git
```

### via SSH
```bash
// create a directory where you want to clone quickiedox
// cd into that directory and run 

git clone git@github.com:mkocansey/quickiedox.git
```

## Run the App

Now that you have cloned the repo, let us run the app to ensure you can see the documentation that 
ships by default.

```bash
composer install
```

```bash
php -S localhost:8000
```

After running the above command you see see output similar to what is below. The version of PHP might differ depending on what you have installed on your machine.

```bash
[Thu Mar  9 00:11:36 2023] PHP 8.2.3 Development Server (http://localhost:8000) started
```

Navigating to `http://localhost:8000` should display the screen below.

&nbsp;


![QuickieDox Homepage](/assets/images/homepage.jpg)

&nbsp;

Clicking on **Read Docs** from the image above should display the screen below.

![QuickieDox Homepage](/assets/images/installation.jpg)

&nbsp;


You can tell from the above image that QuickieDox is unable to load the documentation navigation or the default documentation pages. This is very much expected since **we have not pulled in the markdown files** that make up the documentation. After all that is the whole essence of QuickieDox. To generate documentation from markdown files. 

By default QuickieDox expects the markdown files to be in a `markdown`{.inline} directory at the root of the project. You can use any directory name of your choice but just make sure you update the [config file]({version}/configuration) to tell QuickieDox where to look for your `.md`{.inline} files.

## Pull In The Markdown Files

The markdown files that make up the documentation are expected to sit in a directory you specify. The default is `markdown`{.inline}. The [assumption/convention]({version}/conventions) here is that your markdown files are hosted in their own git repo. There are three ways to pull in the markdown files.

### Just Copy and Paste

All QuickieDox needs to are `.md`{.inline} files in the `markdown`{.inline} directory. You can simple copy and paste your `.md`{.inline} files into this directory and voila! If your documentation is in versions, you will need to have a separate directory for every version number. For example, if your documentation has version 1.x and 2.x, you will need to create a `1.x`{.inline} and `2.x`{.inline} directories in the `markdown`{.inline} directory. You will then need to copy the appropriate `.md`{.inline} files into their respective directories. 
See the [Conventions > Versioning docs]({version}/convention-versions) for more on this.

### Go to This URL

It is possible to pull in your markdown files by visiting the URL below. This assumes you are still running the app from the server we started above via `php -S localhost:8000`{.inline}


[http://localhost:8000/get-markdown](http://localhost:8000/get-markdown)

{.note.alert}
Ensure you have properly modified your QuickieDox [configurations]({version}/configuration) before clicking on the URL above to pull in your markdown files. The route 


### Run This Bash Script

At the root of the project is a `get-markdown.sh`{.inline} shell script containing very few lines of code to clone the repo containing the markdown files. You will need to modify the script and put in the url to your markdown files repo. Next run the script as shown below in a terminal. You need to be at the root of your project.

```bash
./get-markdown.sh
```

Once the markdown files are pulled in, you should be able to see your documentation pages.

&nbsp;
