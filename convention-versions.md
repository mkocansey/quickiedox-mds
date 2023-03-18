# Documentation Versions

QuickieDox works for both versioned and non-versioned documentations. The documentation you’re reading here now is an example of a non-versioned documentation. The dropdown for switching between versions of the documentation is hidden if your docs are non-versioned. 

If you intend to version your documentation there are a few changes you need to make in the `config.php`{.inline} file to tell QuickieDox how to handle your versioning. 

## doc_versions

This variable is only available in the `config.php`{.inline} file and not the .env file. It accepts an array of version numbers you wish to make documentation available for. The content of this array is what is used to populate the dropdown for switching between documentations. QuickieDox does not sort the content of this array. It only displays the values from top to bottom with `$doc_versions[0]`{.inline} listed first in the dropdown and so on until  `$doc_versions[count($doc_versions)]`{.inline}. Below is an example of how to define versions. 

```php
// config.php
...
$doc_versions = [
    '3.0',
    '2.0',
    '1.0',
    '0.1.x'
];
```

&nbsp;

QuickieDox doesn’t perform any validations on the array values. They are displayed as is. 

For non-versioned documentations, `$doc_versions`{.inline} must contain the name of the default branch you will be cloning your markdown from. For example, the QuickieDox documentation is non-versioned but the markdown files are in the `main`{.inline} branch so the `$doc_versions`{.inline} array is defined as:


```php
// config.php
...
$doc_versions = [
    'main'
];
...
```


## default_doc_version

This tells QuickieDox which version of the documentation to display as the default. If an explicit value is not set, the first element in the array is used. 

## Version Numbering and Git

For documentations that are versioned, QuickieDox serves pages by looking for .md files in your `DOCS_DIRECTORY > version_number`{.inline} directory. Where *version_number* is whatever version of the documentation the user has requested. `DOCS_DIRECTORY`{.inline} is defined in the `.env`{.inline} file.

### Pull Versions From Git

As explained [here](installation#pull-in-the-markdown-files), you can pull in the markdown files either by visiting the `/clone`{.inline} route. If you earlier on started the web server built in to PHP with `php -S localhost:8000`{.inline}, the url will be [http://localhost:8000/clone](http://localhost:8000/clone)


{.alert.note}
QuickieDox expects each version you specified in your `doc_versions`{.inline} array to exist **as a branch**. 

Since it is possible for users to have several versions of their documentation with each version possibly having several markdown files, QuickieDox handles cloning of versions using Ajax, one version at a time. It automatically moves on to the next version when one is done, until all versions have been cloned. 
If you navigate away from the */clone* route and come back, QuickieDox will continue from where you left off, after validating your PIN of course. This technique prevents PHP from reaching its `max_execution_time`{.inline} which results in a timeout.

Ideally, cloning your documentation pages should not time out, but, if it does, you can uncomment the line below to increase PHP's execution time. The line can be found in `Controllers/DocController.php : clone()`{.inline}

```php
// config.php
...
- // ini_set('max_execution_time', '300');
+ ini_set('max_execution_time', '300');
...
```

When pulling in markdown files, QuickieDox runs the command below.
```php
...
exec("git clone --branch $version --single-branch $repo_url $version_directory 2>&1");
...
```

If the documentation files already exist, QuickieDox runs the command below instead.

```php
...
exec("git reset --hard origin/$version && git pull && git clean -xdf");
...
```

### Manually Add Versioned Docs

Alternatively you can manually create the directories that correspond to the versions you defined in the `$doc_versions`{.inline} variable. Building up on the example above, we will create two directories  `2.0.0`{.inline} and `1.0.0`{.inline} in the `markdown`{.inline} directory. Next you copy the .md files into their corresponding directories. 

### Switching Between Documentation Versions

Every time a user requests for a documentation page, QuickieDox fetches the corresponding page (.md file) and the `navigation.md`{.inline} page (or whatever file has been defined in `NAV_PAGE`{.inline}) for the version specified. 

Assuming a user is reading *Handling Authentication* in your version 2.0.0 documentation and switches to version 1.0.0, QuickieDox does not fetch the version 1.0.0 version of *Handling Authentication*. It goes to the default documentation page as defined in the .env file and also loads the navigation file available in the version 1.0.0 directory. 

&nbsp;
