# Code Snippets 

Code highlighting in QuickieDox is handled with [Prism](https://prismjs.com). 

## Supported Languages

Prism supports highlighting for several syntaxes but only the following have been compiled into QuickieDox. 

||||
|---|---|---|
| markup (html, svg, xml, mathml, ssml, atom, rss,) | css | clike |
| javascript, js | bash, sh, shell | dart |
| go | js-templates | kotlin, kt, kts |
| perl | php | python, py |
| jsx, tsx | regex | swift |
| typeScript, ts, tsconfig | wasm | |


By default line numbers are disabled when displaying code snippets in QuickieDox. This can be enabled by setting `DISPLAY_LINE_NUMBERS`{.inline} to `true`{.inline} in the `.env`{.inline} file or `display_line_numbers`{.inline} to `true`{.inline} in the `config.php`{.inline} file. It is possible to enable line numbers for individual code snippets using [inline attributes](markdown-attributes). For example.

~~~markdown
```js
{.line-numbers}
setTheme = () => {
	let theme = window.localStorage.getItem('theme') || 'dark';
	document.body.classList.add(theme);
}
```
~~~

The above code snippet will be displayed with line numbers. 


## Code Blocks

Code blocks can be defined either by using the backtick (`) or tilde (~) characters. You will also need to [append the language](#supported-languages) the snippet is in to enable Prism properly perform its highlighting as shown in the examples below:

~~~markdown
```js
	console.log('hello world'):
```
~~~

```markdown
~~~js
    console.log('hello world'):
~~~
```

### Highlight Specific Lines

It is possible to highlight specific lines in a code snippet. This can be achieved by using [inline attributes]({version}/markdown-attributes). 

~~~markdown
{.line-numbers data-line="1,3,5"}
```js
highlightThisPageInNav = () => {
    let this_page = (((location.href).split('/')).slice(-1)[0].split('#'))[0];
    document.querySelectorAll('nav li a').forEach((el) => {
        if (el.getAttribute('href').includes(this_page)) {
            el.classList.add('selected');
        }
    });
}
```
~~~

From the above example we are instructing Prism to highlight lines 1, 3 and 5. It is also possible to highlight a range of lines. 

~~~markdown
{data-line="1-3, 5-10"}
```js
highlightThisPageInNav = () => {
    let this_page = (((location.href).split('/')).slice(-1)[0].split('#'))[0];
    document.querySelectorAll('nav li a').forEach((el) => {
        if (el.getAttribute('href').includes(this_page)) {
            el.classList.add('selected');
        }
    });
}
```
~~~

## Inline Code

There are times when you just need to highlight code inline instead of an entire block of code. For example, you want to highlight a configuration variable. Again, QuickieDox uses inline attributes to achieve this. Let’s look at an example:

```markdodwn
You can simply run `composer install`{.inline} to pull in packages
```

You can simply run `composer install`{.inline} to pull in packages

{.alert.tip}
You can enable line numbers for all code blocks in your project by setting `DISPLAY_LINE_NUMBERS=true`{.inline} in the `.env`{.inline} file.

&nbsp;
