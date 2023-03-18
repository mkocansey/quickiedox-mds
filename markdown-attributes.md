# Inline Attributes

This document will not focus on teaching markdown since it is expected you already know some basic markdown syntax. 

It is possible to include HTML tags in your markdown but QuickieDox strips out HTML and parses mostly acceptable markdown tags and return them as HTML. The stripping of HTML tags is done by setting `ALLOW_HTML_IN_MARKDOWN=false`{.inline}. Set this to true if you want to allow the HTML tags you have in your markdown files.

That said, QuickieDox provides a way to include inline CSS targeted at specific elements in your markdown. This is achieved using [this feature](https://commonmark.thephpleague.com/2.3/extensions/attributes/) available in CommonMark. You can then style these inline classes in your own css files or in `src/index.css`{.inline}. 

There are two ways to attach styles and classes to elements. The most common methods are:

## Above the Element

```markdown
{.uppercase}
This is a paragraph with the class uppercase
```

The above will result in the following HTML after parsing.
```html
<p class="uppercase">
    This is a paragraph with the class uppercase
</p>
```

You can even set multiple classes on the element. 

```markdown
{.uppercase .purple}
This is a paragraph that's all uppercase and purple 
```

The above will result in the following HTML after parsing.
```html
<p class="uppercase purple">
    This is a paragraph with the class uppercase
</p>
```

Instead of classes, you can also set IDs on block level elements. 

```markdown
{#page-title}
This paragraph will have the ID page-title
```

The above will result in the following html after parsing.
```html
<p id="page-title">
    This is a paragraph with the class uppercase
</p>
```

You can even do both classes and IDs on the elements. 

```markdown
`{#page-title .uppercase .purple}
This is a paragraph that's all uppercase and purple with the ID as page-title. 
```

The above will result in the following HTML after parsing
```html
<p id="page-title" class="uppercase purple">
     This is a paragraph that's all uppercase and purple with the ID as page-title. 
</p>
```

It makes sense to apply classes to elements that are repeated throughout your documentation that need to have the same styling. In one-off cases where you want to set some styling to a block element, you can set the `style`{.inline} attribute as shown below.  

```markdown
{style="line-height: 2"}
The text in this paragraph needs to breathe. 
Every other paragraph needs to be air tight. 
```

The above will result in the following HTML after parsing
```html
<p style="line-height: 2">
     The text in this paragraph needs to breath. 
     Every other paragraph needs to be air tight. 
</p>
```

We can even mix all three together.

```markdown
{style="line-height: 2" #all-three .uppercase .purple}
Just putting into practice all that we have learnt so far. Nice!! 
```

The above will result in the following HTML after parsing.
```html
<p style="line-height: 2" id="all-three" class="uppercase purple">
	Just putting into practice all that we have learnt so far. Nice!!
</p>
```


## As In-line 

Defining classes, IDs and styles inline means they apply to inline elements and not block level elements as explained earlier above. Let's take the example below. 

 ```markdown
This is a paragraph with this `word`{.text-red-400} as red for emphasis. 
```


The above will result in the following HTML after parsing.

```html
<p>
	This is a paragraph with this 
	<code class="text-red-400">word</code> as red for emphasis.
</p>
```

You can see from above, the styling is only applied to one word and not the entire `<p>`{.inline} tag. The same logic explained earlier for applying IDs and styles also applies to inline elements. 

```markdown
This is an example showing how to make me **bold and bright**{style="color: lime"}
```


The above will result in the following HTML after parsing.
```html
<p>
	This is an example showing how to make 
	me <strong style="color: lime">bold and bright</strong>
</p>
```

{.alert.stop}
Inline styles and classes don't seem to work for all elements. Just putting the attributes after a word for example will not create a \<span\>. See more on [markdown attributes](https://commonmark.thephpleague.com/2.3/extensions/attributes/).

## It's Not Just CSS Attributes

The attribute definitions are not limited to just classes, IDs and styles. You can define any attribute on an element. 

```markdown
{data-nav="download" aria-label="download"}
Download all our lesson notes today.
```


The above will result in 

```html
<p data-nav="download" aria-label="download">
	Download all our lesson notes today.
</p>
```

Let's take a look at a table example with an `align`{.inline} attribute on the table heading.

```markdown
| Product | Description {align="absmiddle"} |
| ------- | ----------- |
| iPhone 14 Pro | You know what it is |
```

The above will result in the following.

```html
<table>
	<thead>
		<tr>
			<th>Product</th>
			<th align="absmiddle">Description</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>iPhone 14 Pro</td>
			<td>You know what it is</td>
		</tr>
	</tbody>
</table>
```