# TailwindCSS Customization

QuickieDox uses TailwindCSS for its styling. The source css file is defined in `src > index.css`{.inline} and can be modified to suit your theme needs. The default theme colour used by QuickieDox is `indigo`{.inline}. 

To change this to a different theme colour simply edit the value for primary in the `tailwind.config.js`{.inline} file  as shown below. Let's say you want to change from indigo to purple.

{.line-numbers}
```js
...
colors: {
-   primary: colors.indigo,
+   primary: colors.purple,
}, 
...
```

To compile your changes run this command from the root of your project. 

{.command-line}
```bash
npx tailwindcss -i ./src/index.css -o ./assets/css/quickiedox.css --watch
```

To compile your changes for production run the command below

{.command-line}
```bash
npx tailwindcss -i ./src/index.css -o ./assets/css/quickiedox.css --minify
```