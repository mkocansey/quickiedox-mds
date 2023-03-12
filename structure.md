# Directory Structure

QuickieDox has a very lean directory structure. This is possible because it is not tied to any framework. Below is a list of the directories and files that make up QuickieDox.

| Directory | Files | Description |
| :--- | :--- | :--- |
| `Root Directory`{.inline} {nowrap="nowrap"} | index.php | Entry point of the app. Loads and sets environment variables as well as routes |
| | config.php | Configurable variables that get loaded and used throughout the app |
| | .env | Encironment variables |
| | deploy-example.php | Example deployment script to help deploy documentation to production or test server. Requires deployer/deployer package. |
| | composer.json | List of packages to pull in to app |
| | routes.php | Defines routes used in loading different pages in the app |
| | tailwind.config.js | TailwindCSS configuration file |
| `assets > css`{.inline} | animate.min.css | css file for animating navigation items |
| | prism.css | css file for handling code highlighting |
| | quickiedox.css | main css file for the app |
| `assets > images`{.inline} {nowrap="nowrap"} | | contains image files used in the app |
| `assets > js`{.inline} | prism.js| javascript file for code highlighting |
| | quickiedox.js | main js file for the app |
| `Controllers`{.inline} | DocController.php| handles interaction between the user interface and the backend |
| `Core`{.inline} | App.php| sets and gets variables that are available throughout the app |
| | bootstrap.php | loads in all configuration variables and sets them globally using App.php |
| | Doc.php | handles manipulation of md files for reading |
| | Envy.php | handles reading of variables from .env file |
| | helpers.php | helper functions for performing repeated functions |
| | Request.php | handles url requests |
| | Router.php | handles routing mechanism |
| | Session.php | sets and unsets session variables. Sessions here are mostly url parameters |
| `markdown`{.inline} | | .md files are pulled in here by default |
| `src`{.inline} | index.css | source css file before it is compiled to assets/css/quickiedox.css |
| `vendor`{.inline} | | composer packages are pulled in here |
| `views`{.inline} | 404.md | default 404 page. Used when pages are missing. This is placed in the views directory instead of markdown becuase the file needs to always be available even if the user decides to load their md files into a directory other than `markdown`{.inline} |
| | home.php | default homepage |
| | reader.php | layout page for displaying documentation for reading |
