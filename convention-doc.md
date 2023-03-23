# Documentation Files

The documentation pages must all be markdown files ending with the file extension .md. The documentation files should ideally also be hosted in a git repository.

Any external links you define automatically open in a new tab/window. QuickieDox checks the url of the link, if it contains *http*, `target="blank"`{.inline} is appended to the link.

## Sub Navigation

Sub navigations are a quick way to jump to portions within a document. Think of this as a table of contents of some sort. You do not need to define these sub navigations. QuickieDox does this automatically by looking at the various headings defined within the documentation file and generating a sub navigation for/from them.

## Updating Documentation

If you make changes ONLY to your .md files, assuming they are pulled in from their own repository, you wouldn't need to deploy the website again. All you need to do is go to the `/clone`{.inline} route from your documentation website url. Assuming your website documentation website is hosted at http://docs.myapi.com, going to http://docs.myapi.com/clone should allow you to pull in the updated documentation (.md files).

## Documentation Font

The documentation pages are currently displayed using the Inter font available from [Google Fonts](https://fonts.google.com/specimen/Inter). QuickieDox makes it easy for you to change the font used for displaying documentation text in two simple steps.

### Import the font you want to use

This is done in the header.php file. This is an include file that sits above all the presentation pages.

```html
// views/header.php
...
<link 
	rel="stylesheet" 
	href="https://fonts.googleapis.com/css2?family=Inter:...">
...
```


### Change the font declaration in index.css

```css
// src/index.css
...
.doc-font {
-  font-family: 'Inter', sans-serif;
+  font-family: 'my-new-font-name', sans-serif;
}
...
```

### Recompile the CSS file

Run this from the root of your QuickieDox project.

{.command-line}
```bash
npx tailwindcss -i ./src/index.css -o ./assets/css/quickiedox.css --minify
```

## Use Your Logo

Yes you can. The default is the QuickieDox logo but if you want to make this yours and brand it as yours, you will need to change the logo. The default is in `assets/images/logo.svg`{.inline}. You can simply replace the logo file with the same file name and your logo will immediately take effect. Alternatively, you can upload your image to the same `assets/images/`{.inline} directory and update `views/reader.php`{.inline} with the file name of your logo.

```html
- <img src="/assets/images/logo.svg" alt="QuickDox Logo" ... />
+ <img src="/assets/images/my-new-logo.png" alt="MKO Logo" ... />
```

&nbsp;
