# Protecting Documentation Pages

There are instances where you want readers to be logged in before accessing the documentation pages. QuickieDox does not implement user authentication but provides an `Auth.php`{.inline} page with a method `canRead`{.inline} that returns `true`{.inline} or `false`{.inline}. 

When `REQUIRE_SIGNIN`{.inline} in the .`env`{.inline} file is set to `true`{.inline}, the `Doc->read()`{.inline} method responsible for rendering the documentation pages calls `Auth->canRead()`{.inline} and allows access to the page if the return value is `true`{.inline}, otherwise the content of `views/auth-required.md`{.inline} are displayed. 

## In Summary

To ensure only authenticated users can access your docs:
1. Set `REQUIRE_SIGNIN=true`{.inline} in the .env file. 
2. Edit `Controllers/AuthController.php`{.inline} and `Core/Auth.php`{.inline} and implement your authentication logic. 
3. Define appropriate routes in `routes.php`{.inline} to handle the page interactions. 
4. Ensure the `canRead()`{.inline} method in `Auth.php`{.inline} returns true if a user is authenticated and false if a user is not. 


## Whitelisting Pages

Setting `REQUIRE_SIGNIN=true`{.inline} in the .env file affects every markdown file that makes up your docuemntation. Meaning, any page the user tries to read will check if they are signed in. It is possible to define files that will always be accessible and excluded from this check.  

```bash
# .env
...
REQUIRE_SIGNIN=true
...
```

```php
// config.php
...
'whitelisted_docs'  => [
	'installation.md',
	'getting-started.md',
	'known-issues.md'
],
...

```

The files listed in `whitelisted_docs`{.inline} above will always be available for reading.