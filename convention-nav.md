# The Navigation File

It is important to follow a few QuickieDox conventions to ensure your documentation content is served effortlessly. The navigation is what drives all your documentation content. Content of this file is displayed in the left section of your documentation pages. If you learn quicker by seeing and doing, [take a look at this website's navigation file.](https://raw.githubusercontent.com/mkocansey/quickiedox-mds/main/navigation.md)

## The File Name

The navigation file by default is expected to be named `navigation.md`{.inline}. This is however available as a configurable variable `NAV_PAGE`{.inline} in the `.env`{.inline}. QuickieDox looks for this file in your `markdown`{.inline} directory (or whatever directory you have defined in `DOCS_DIRECTORY`{.inline}) and parses its content to present the navigation items.

Assuming your documentation will be in [versions](convention-versions), you will need to have a navigation file in each version directory since each version may have different navigation items. Again, the navigation file in each version directory must correspond to the file name defined in the `NAV_PAGE`{.inline} variable. For example, a version 2.0 `navigation.md`{.inline} file may have a link that says ***How to upgrade from 1.x***. A link that will likely not be available in the version 1.0 `navigation.md`{.inline} file.



## You Need Top Level Items

Top level menu items serve as parents for everything else beneath them. These items are what users click on to reveal what links are available. They need to be defined as list items and heading ones(`<h1>`{.inline}) usiing markdown syntax of course. For example, the following are the top level items in the QuickieDox documentation: 

* Getting Started
* Customization
* Conventions
* Markdown Syntax

```markdown
* # Getting Started
* # Customization
* # Conventions
* # Markdown Syntax
```


## Everything Here is a List Item

Every navigation item must be defined as a list item using markdown syntax, including the top level items even though they only expand and collapse when clicked on. In code, the resulting `<li>`{.inline} items are parsed and formatted with CSS.

```markdown
* # Getting Started
	* [Installation](installation)
```

## Each URL Must Correspond to a Markdown File

Let us take a look at a few lines from a navigation file

```markdown
* # Getting Started
	* [Installation](installation)
	* [How This Works](how-this-works)
```

From the example above you will notice that the url for **Installation** is `installation`{.inline}. The url for **How This Works** has also been defined as `how-this-works`{.inline}.  QuickieDox will expect to actually find the following files in your markdown directory:

* `installation.md`{.inline}
* `how-this-works.md`{.inline}

You will notice the URLs have no **.md** file extensions. The URLs also have no connection to their versions. QuickieDox handles all the mappings in the background. 

{.alert.tip}
The rule for navigation item URLs is very simple. The URL should ONLY be the name of the corresponding **.md** file without the **.md** file extension.

## Nesting Is Based On Headings and Indentation

The very top level navigation items are defined as heading ones. To achieve nested navigation items, you will need to increase the heading numbers and their indention under their parent headings. All heading two items are nested under their parent heading one. All heading three items are nested under their parent heading two. All headings with the same number are available at the same level under their parent heading. Any navigation item that will have children beneath it must be a heading and not linked. See the example below.

```markdown

* # Sample Nested Nav

	* ## Level One
		* [Designing APIs](api-design)
		* [Authenticate Users](authentication)
    
	* ## Level Two
		*  [Save User](user-save)
		*  [user Details](user)
		*  [List All Users](users)
		*  [Delete User](user-delete)
           
        *  ### Level Three
            *  [Profile](user-profile)
            *  [Awards](user-awards)
            *  [Favorites](user-favs)

```

&nbsp;

