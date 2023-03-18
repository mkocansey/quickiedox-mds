# Tables

You should already know how to create tables using markdown so this page won't focus on that. In fact, [this article](https://www.markdownguide.org/extended-syntax/#tables) does that well. This page only highlights a few tricks you can employ to take advantage of some helpers included in QuickieDox. 

## Empty Table Headings

As you may already know, it is not possible to define a table in markdown without providing the table headings. There are cases where you really don't want a heading for your table. Let's take for example a section of an API documentation that talks about the endpoint URLs and method in a table as shown below. 

| Heading 1 | Heading 2 |
|---|---|
| Test URL | https://test.api.quickiedox.com/user/delete |
| Production URL | https://api.quickiedox.com/user/delete |
| Method | **POST** |

You really wouldn't want to give such a table a header row but markdown forces you to. 

QuickieDox allows you to specify empty table headings that get stripped out using CSS. The above table will now become:

|||
|---|---|
| Test URL | https://test.api.quickiedox.com/user/delete |
| Production URL | https://api.quickiedox.com/user/delete |
| Method | **POST** |


The resulting table as you can tell from above has no table headings. 

## Aligning Cells

By default content in cells are left aligned and QuickieDox leaves it at that. Table headings are by default centre aligned. Again, QuickieDox does not mess with that. There are standard ways in markdown to align content in cells. 

### Left Alignment 

#### OPTION 1

```markdown
| User Role | Description |
| :--- | :---|
| Super admin | Has Spider-Man powers |
| Admin | Spider-Man's secretary |
```

| User Role | Description |
| :--- | :---|
| Super admin | Has Spider-Man powers |
| Admin | Spider-Man's secretary |


The colon (:) specified before the three dashes tells markdown to left align the table heading content.  This is one way to do this. 

#### OPTION 2

Following the tips [specified here]({version}/convention-css), it is possible to also define the alignment inline as shown below. Option 1 is actually simpler. 

```markdown
| User Role {style="text-align: left"} | Description {.align-left} |
| -—- | -—-|
| Super admin | Has Spider-Man powers |
| Admin | Spider-Man's secretary |
```

| User Role {style="text-align: left"} | Description {.align-left} |
| --- | --- |
| Super admin | Has Spider-Man powers |
| Admin | Spider-Man's secretary |

From the example above you can tell the second column heading has been assigned a class `align-left`{.inline}. This assumes you have already defined this class in your css file to left align elements/content. QuickieDox has no such class defined so the desciption column stays centre aligned.

### Right Alignment 

#### OPTION 1

```markdown
| User Role | Description |
| ---: | ---: |
| Super admin | Has Spider-Man powers |
| Admin | Spider-Man's secretary |
```

| User Role | Description |
| ---: | ---: |
| Super admin | Has Spider-Man powers |
| Admin | Spider-Man's secretary |

The colon (:) specified after the three dashes tells markdown to right align the table heading content.  This is one way to do this. Right aligning a column heading also right aligns the entire column.

#### OPTION 2

Following the tips [specified here]({version}/convention-css), it is possible to also define the alignment inline as shown below. Again, option 1 is simpler. 

```markdown
| User Role {style="text-align: right"} | Description {.align-right} |
| --- | --- |
| Super admin | Has Spider-Man powers |
| Admin | Spider-Man's secretary |
```

From the example above you can tell the second column heading has been assigned a class `align-right`{.inline}. This assumes you have already defined this class in your css file to right align elements/content. 

### Centre Alignment 

#### OPTION 1

```markdown
| User Role | Description |
| :—-: | :—-: |
| Super admin | Has Spider-Man powers |
| Admin | Spider-Man's secretary |
```

| User Role | Description |
| :---: | :---: |
| Super admin | Has Spider-Man powers |
| Admin | Spider-Man's secretary |

The colon (:) specified at the left and right ends of the three dashes tells markdown to centre align the table heading content.  This is one way to do this. Centre aligning a column heading also centre aligns the entire column.

#### OPTION 2

Following the tips [specified here]({version}/convention-css), it is possible to also define the alignment inline as shown below. 

```markdown
| User Role {style="text-align: center"} | Description {.align-center} |
| -—- | -—-|
| Super admin | Has Spider-Man powers |
| Admin | Spider-Man's secretary |
```

From the example above you can tell the second column heading has been assigned a class `align-center`{.inline}. This assumes you have already defined this class in your css file to center align elements/content. 

Read this article to learn more about [how to define tables in markdown](https://www.markdownguide.org/extended-syntax/#tables). 

&nbsp;