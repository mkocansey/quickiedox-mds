# Documentation Files

The documentation pages must all be markdown files ending with the file extension .md. The documentation files should ideally also be hosted in a git repository.

Any external links you define automatically open in a new tab/window. QuickieDox checks the url of the link, if it contains *http*, `target="blank"`{.inline} is appended to the link.
## Sub Navigation
Sub navigations are a quick way to jump to portions within a document. Think of this as a table of contents of some sort. You do not need to define these sub navigations. QuickieDox does this automatically by looking at the various headings defined within the documentation file and generating a sub navigation for/from them.

## Updating Documentation
If you make changes ONLY to your .md files, assuming they are pulled in from their own repository, you wouldn't need to deploy the website again. All you need to do is go to the `/get-markdown`{.inline} route from your documentation website url. Assuming your website documentation website is hosted at http://docs.myapi.com, going to http://docs.myapi.com/get-markdown should allow you to pull in the updated documentation (.md files).