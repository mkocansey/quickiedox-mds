# Overview


QuickieDox is a **purely vanilla PHP** project that allows you to quickly create elegant documentation from markdown files and works with PHP >= 7.4. Not being tied to any framework makes QuickieDox as lightweight as possible.

To use QuickieDox you must already know how to write markdown syntax and also have some very basic knowledge of PHP. [This guide](https://www.markdownguide.org/getting-started/) can help refresh your markdown knowledge.

## The Ideal Use Case

QuickieDox is ideal for projects with documentation needs. This may necessarily not be a technical project. QuickieDox gives you a headstart with an already beautifully designed documentation website that only requires your markdown files for it to work.

{.alert.stop}
QuickieDox is not provided as software as a service and does not host your documentation. You will need to host everything yourself just like you would host any of your websites. 

## Installation 

To create your own documentation website, simply [**clone the repo**](https://github.com/mkocansey/quickiedox-mds/archive/refs/heads/main.zip) and begin your [customization](customize-home). You can clone QuickieDox using one of these two methods.

### Via Composer

The easiest is to create a QuickieDox project using composer by running the command below.

```bash
# replace your-project-name with the name of the directory you want created
# or the name of your project (directory will be created if it does not exist)
```
```bash
composer create-project mkocansey/quickiedox your-project-name
```

### Clone From GitHub

#### via HTTPS

```bash
# create a directory where you want to clone quickiedox
# cd into that directory and run 
```
{.command-line}
```bash
git clone https://github.com/mkocansey/quickiedox.git
```

#### via SSH
```bash
# create a directory where you want to clone quickiedox
# cd into that directory and run 
```
{.command-line}
```bash
git clone git@github.com:mkocansey/quickiedox.git
```

### Rename .env-example

You will find a `.env-example`{.inline} file at the root of the project you just cloned. Rename `.env-example`{.inline} to `.env`{.inline}. The app will not run if this is not done.

## Run the App

Run the app to ensure you can see the documentation that ships by default. From the root of the directory you just cloned, run:

{.command-line}
```bash
composer install
```

Let's start an inbuilt PHP server to quickly test what you just cloned.

{.command-line}
```bash
# this assumes port 8000 is not in use by another site or app
php -S localhost:8000
```

After running the above command you should see output similar to what is below. The version of PHP will reflect what you have installed on your machine.

```bash
[Thu Mar  9 00:11:36 2023] PHP 8.2.3 Development Server (http://localhost:8000) started
```

Navigating to [http://localhost:8000](http://localhost:8000) should display the screen below.

&nbsp;


![QuickieDox Homepage](/assets/images/homepage.jpg)

&nbsp;

Clicking on **Read Documentation** from the home page as shown in the image above should display the screen below.

![QuickieDox Homepage](/assets/images/installation.jpg)

&nbsp;


You can tell from the above image that QuickieDox is unable to load the documentation navigation or the default documentation page. This is very much expected since **we have not pulled in the markdown files** that make up the documentation. After all that is the whole essence of QuickieDox. To generate documentation from markdown files. 

## Pull In The Markdown Files

By default QuickieDox expects the markdown files to be in a `markdown`{.inline} directory at the root of the project. You can use any directory name of your choice but just make sure you update the [config file](customize-config) to tell QuickieDox where to look for your `.md`{.inline} files. 

{.alert.note}
The directory to clone the .md files into is not included by default. QuickieDox tries to create this directory when cloning the .md files and will require the appropriate permissions. If QuickieDox is unable to create the dorectory you will need to manually create the directory, change either the owner or group to the user PHP runs as. On most linux systems this is `www-data`{.inline}. Lastly you this this directory owner or group write permissions.

As mentioned earlier, the markdown files that make up the documentation are expected to sit in a directory you specify. The default is `markdown`{.inline}. The [convention](convention-doc) here is that your markdown files are hosted in their own git repo. There are two ways to pull in the markdown files.

### Use The Inbuilt Cloning Tool

It is much easier to pull in your markdown files using the cloning URL that is built into QuickieDox. Assuming you are still running the app from the server we started above using `php -S localhost:8000`{.inline}, you will need to visit the URL below.


[http://localhost:8000/clone](http://localhost:8000/clone)

{.stop.alert}
Ensure you have modified the QuickieDox [configurations](customize-config) before pulling in your markdown files. The URL will ask for the PIN defined for `GIT_CLONE_PIN`{.inline} in the `.env`{.inline} file. You won't be able to use this URL if your PIN is blank.

### Just Copy and Paste

QuickieDox only needs `.md`{.inline} files in the `markdown`{.inline} directory or the directory you specified in `DOCS_DIRECTORY`{.inline}. You can simple copy and paste your `.md`{.inline} files into this directory and voila! If your documentation is in versions, you will need to have a separate directory for every version. For example, if your documentation has version 1.5 and 2.2, you will need to create `1.5`{.inline} and `2.2`{.inline} directories in the `markdown`{.inline} directory. You will then need to copy the appropriate `.md`{.inline} files into their respective directories. 
See the [Conventions > Versioning docs](convention-versions) for more on versioning.

&nbsp;
