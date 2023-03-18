# Customize the Homepage

The default behaviour of QuickieDox is to load a home page. There is a button that then leads to the main documentation page. Landing on the home page can be skipped by setting `SHOW_INDEX_PAGE=false`{.inline} in your `.env` file. Users will be directed straight to the page you’ve defined in the `DEFAULT_DOC_PAGE`{.inline} variable. 

The content of the home page can be found in `views/home.php`{.inline} at the root of the project. Simply edit this page to suit your design needs. The default QuickieDox home page is quite minimal. It displays an image from [Storyset](https://storyset.com) with text styled using [TailwindCSS](https://tailwindcss.com). 

You can change your theme colours by [following this](customize-tailwind) guide.

Use the link below on any button or link on your home page that you want to take users to your main documentation page.

```php
<a href="<?php echo docs_home(); ?>">
    link or button goes here
</a>
```

&nbsp;
