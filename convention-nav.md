# The Navigation File

There are a few conventions to follow to ensure your documentation content is served with very little effort. The navigation is what drives all your documentation content. Content of this file is displayed in the left section of your documentation pages. If you learn quicker by seeing and doing, [take a look at this navigation file.](https://github.com/mkocansey/quickiedox)

## The File Name

The navigation file **must** be named `navigation.md`{.inline}. This is not available as a configurable option. QuickieDox looks for this file in your `markdown`{.inline} directory and parses its content to present the navigation items.

Assuming your documentation will be in versions, you will need to have a `navigation.md`{.inline} file in each version directory since each version may have different navigation items. For example, a version 2.0 `navigation.md`{.inline} file may have a link that says ***How to upgrade from 1.x***. A link that will likely not be available in the version 1.0 `navigation.md`{.inline} file



## You Need Top Level Items

Top level menu items serve as parents for everything else beneath them. These items are what users click on to reveal what links are available. They need to be defined as list items and markdown `<h1>`{.inline}. For example, the following are the top level items in the QuickieDox documentation: 

* Getting Started
* Customization
* Markdown Syntax
* Sample Nested Nav

```markdown
* # Getting Started
* # Customization
* # Markdown Syntax
```


## Everything Here is a List Item

Everynavigation item must be defined as a list item using markdown syntax, including the top level items even though they only expand and collapse when clicked on. In code, the resulting `<li>`{.inline} items are parsed and formatted with CSS.

```markdown
* # Getting Started
	* [Installation]({version}/installation)
```


## Each URL Must Correspond to a Markdown File

Let us take a look at a few lines from a navigation file

```markdown
* # Getting Started
	* [Installation]({version}/installation)
	* [How This Works]({version}/how-this-works)
```

From the example above you will notice that the url for **Installation** is `{version}/installation`{.inline}. The url for **How This Works** has also been defined as `{version}/how-this-works`{.inline}.  QuickieDox will expect to actually find the following files in your markdown directory:

* `installation.md`{.inline}
* `how-this-works.md`{.inline}



## Nesting Is Based On Headings and Indentation

The very top level navigation items are defined as heading ones. To achieve nested navigation items you will need to increase the heading numbers and their indention under their parent heading. All heading two items are nested under their parent heading one. All heading three items are nested under their parent heading two. All headings with the same number are available at the same level under their parent heading. Any navigation item that will have children beneath it must be a heading and not a link. See the example below.

```markdown

* # Sample Nested Nav

	* ## Level One
		* [Designing APIs]({version}/api-design)
		* [Authenticate Users]({version}/authentication)
    
	* ## Level Two
		*  [Save User]({version}/user-save)
		*  [user Details]({version}/user)
		*  [List All Users]({version}/users)
		*  [Delete User]({version}/user-delete)
           
        *  ### Level Three
            *  [Profile]({version}/user-profile)
            *  [Awards]({version}/user-awards)
            *  [Favorites]({version}/user-favs)

```


## Version Numbers Are Optional

