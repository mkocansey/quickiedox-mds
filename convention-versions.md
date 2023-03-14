# Documentation Versions

QuickieDox works for both versioned and non-versioned documentations. The documentation you’re reading here now is an example of a non-versioned documentation. All the markdown files are placed directly in the directory specified in `default_docs_directory`{.inline}. The drop-down for switching between versions of the documentation is hidden if your docs are non-versioned. 

If you intend to version your documentation there are a few changes you need to make in the `config.php`{.inline} file to tell QuickieDox how to handle your versioning. 

## $doc_versions

This variable is only available in the `config.php`{.inline} file and not the .env file. It accepts an array of version numbers you wish to make documentation available for. The content of this array is what is used to populate the drop-down for switching between documentations. QuickieDox does not sort the content of this array. It only displays the values from top to bottom with `doc_versions[0]`{.inline} being listed first in the drop-down and so on until  `doc_versions[$x]`{.inline}. Below is an example of how to define versions. 

```php
$doc_versions = [
    '3.0',
    '2.0',
    '1.0'
];
```

QuickieDox doesn’t perform any validations on the array values. They are displayed as is. 

## $default_doc_version

This tells QuickieDox which version of the documentation to display by default. If an explicit value is not set, the first element in the array is used. 

## Version Numbering and Git

For documentations that are versioned, QuickieDox serves pages by looking for .md files in your `default_doc_directory > version_number`{.inline} directory. Where *version_number* is whatever version of the documentation the user has requested. 

### Pull Versions From Git

As explained [here]({version}/architecture), you can pull in the markdown files either by visiting this URL (http://localhost:8000/get-markdown) if you started the web server with `php -S localhost:8000`{.inline} or by running the shell script below in a terminal from the root of your project. 

{.command-line}
```bash
./get-markdown.sh 
```

QuickieDox expects each version you specified in your `doc_versions`{.inline} array to exist as a branch. QuickieDox loops over the doc_versions array and performs a git checkout of each version number as a branch. 

```php
$doc_versions = [
    '2.0.0',
    '1.0.0'
];

$repo_url = App::get('repo_url');
$markdown_directory = App::get('default_doc_directory');

foreach ($doc_versions as $branch) {
    exec("cd $markdown_directory");
    exec("git checkout $repo_url —$branch");
}
```

### Manually Add Versioned Docs

Alternatively you can manually create the directories that correspond to the version numbers you defined in the `$doc_versions`{.inline} variable. Building up on the example above, we will create a directory called `2.0.0`{.inline} and `1.0.0`{.inline} in the `markdown`{.inline} directory. Next you copy the .md files into their corresponding directories. 

### Switching Between Documentation Versions

Every time a user requests for a documentation page, QuickieDox fetches the corresponding page and the `navigation.md`{.inline} page. 

Assuming a user is reading *Handling Authentication* in your version 2.0.0 documentation and switches to version 1.0.0, QuickieDox does not fetch the version 1.0.0 version of *Handling Authentication*. It goes to the default documentation page as defined in the .env file and also loads the navigation.md files available in the version 1.0.0 directory. 