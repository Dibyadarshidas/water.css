<p align="center">
  <!-- <a href="https://www.npmjs.com/package/water.css"><img align="center" src="https://img.shields.io/npm/v/water.css.svg" alt="NPM page"></a> -->
  <a href="https://www.reddit.com/r/webdev/comments/b9m6mv/watercss_a_collection_of_neat_styles_for_simple/"><img align="center" src="https://img.shields.io/badge/on-reddit-orange.svg" alt="On Reddit"></a>
  <a href="https://www.producthunt.com/posts/water-css"><img align="center" src="https://img.shields.io/badge/on-product%20hunt-red.svg" alt="On Product Hunt"></a>
  <a href="https://github.com/kognise/water.css/blob/master/LICENSE.md"><img align="center" src="https://img.shields.io/github/license/kognise/water.css.svg" alt="MIT license"></a>
</p>

<br>

<h1 align="center">Water.css</h1>
<p align="center">🌊 A drop-in collection of CSS styles to make simple websites just a little nicer</p>

[![Water.css](logo.svg)](https://watercss.netlify.com/)

<br>

## Goals

- Responsive
- Themeable
- Good browser support (works on my old kindle's browser :P)
- Tiny size
- Beautiful
- No classes

## Why?

I commonly make quick demo pages or websites with simple content. For these, I don't want to spend time styling them but don't like the ugliness of the default styles.

Water.css is a CSS framework that doesn't require any classes. You just include it in your `<head>` and forget about it, while it silently makes everything nicer.

## Who?

You might want to use Water.css if you're making a simple static page or demo website that you don't want to spend time styling.

Although it originally wasn't built for more complex websites, many developers have used Water.css as a base stylesheet and creatively applied custom styles to build out an entire app. Nothing is stopping you from doing the same!

## How?

Just stick this in your `<head>`:

### 🌙/☀ Automatic Theme:

`<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/water.css@2/dist/water.min.css">`

### 🌙 Dark Theme:

`<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/water.css@2/dist/dark.min.css">`

### ☀ Light Theme:

`<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/water.css@2/dist/light.min.css">`

<br>

### Other options:

> ⚡ An interactive version selection is available [on the **demo page**!](https://watercss.netlify.com/#installation)

#### Enforce a theme and ignore `(prefers-color-scheme)`

For the main `water.css` file, dark is only treated as a _default theme_: if a user has a preference for either dark or light mode on their device, the stylesheet will respect this. This detection is made possible through a recent CSS media query called `prefers-color-scheme`. If you want to avoid this behavior and enforce dark or light theme, use either `dark.css` or `light.css`.

#### Want to support Internet Explorer?

Both `dark.css` and `light.css` support Internet Explorer 11, but the main `water.css` file **does not** due to lack of `prefers-color-scheme` support.

Be aware that IE also doesn't support [runtime theming](#theming), and fixed fallback values will be used. If you want to override the Water.css theme, we recommend that you [compile your own theme](#compiling-your-own-theme).

#### Unminified builds

All versions are also available as unminified stylesheets, which can be handy during development.  
Simply remove the `.min` from the file name.

## Theming

Do you want to make some adjustments or build your own theme completely different from the official dark or light themes? Since Water.css is built with CSS variables this is super easy to do!
You can find a full list of the variables used at [**src/variables-\*.css**](https://github.com/kognise/water.css/tree/master/src/variables-dark.css).

### Runtime theming

> ⚠ If you use a version with support for legacy browsers like Internet Explorer, skip to [Compiling your own theme](#compiling-your-own-theme)!

Water.css uses Custom Properties (_"CSS variables"_) to define its base styles such as colors. These can be changed and overwritten right in the browser.

Because of this, you can simply add your own stylesheet to the page and set your own CSS variables there. As long as your stylesheet comes after Water.css in the HTML, your values will override the default ones and your theme is applied!

This short example will use Water.css, but color all links red:

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/water.css@2/dist/water.min.css" />
<style>
  :root {
    --links: red;
  }
</style>
```

If you want to change a value for dark or light mode only, use a media query like this:

```html
<style>
  :root {
    --links: yellow; /* Always applied */
  }

  @media (prefers-color-scheme: light) {
    :root {
      --links: blue; /* Only applied in light mode (overrides yellow) */
    }
  }
</style>
```

### Compiling your own theme

If you are targeting browsers without support for CSS Custom Properties such as Internet Explorer, runtime theming is not an option. To apply your own theming, you'll need to make your changes in the source files themselves, then re-compile the CSS files. This works like the following:

- Clone the repository to your machine
- Run `yarn` to install dependencies
- Make the theming changes you want in `src/variables-*.css`
- Run `yarn build` to compile the CSS files
- Use the compiled files in the `dist/` directory on your site

You also might want to check out the [Contributing Guide](https://github.com/kognise/water.css/tree/master/.github/CONTRIBUTING.md) as it contains further information about the build setup.

## Contributing

Water.css becomes better for everyone when people like you help make it better!

Have any questions or concerns? Did I forget an element or selector? Does something look ugly? Feel free to submit an issue or pull request.

If you decide to contribute, after downloading a copy of the repository make sure to run `yarn` to install dependencies useful for development. Then, you can run the following to start a server of the demo with live reloading on change.

```
$ yarn dev
```

**Alternatively, just click this button to develop in Repl.it, a supercool in-browser IDE!** [![Run on Repl.it](https://repl.it/badge/github/kognise/water.css)](https://repl.it/github/kognise/water.css)

Before submitting your first pull request, make sure to check out our [Contributing Guide](https://github.com/kognise/water.css/tree/master/.github/CONTRIBUTING.md)!  
Thanks for taking the time to contribute :)