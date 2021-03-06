# PostCSS Viewport Height Correction

[PostCSS] plugin to correct viewport height value `vh` to real viewport height as stated by CSS Tricks in article https://css-tricks.com/the-trick-to-viewport-units-on-mobile/.

```css
.foo {
    /* Input example */
    height: 100vh;
}
```

```css
.foo {
  /* Output example */
  height: 100vh;
  height: calc(var(--vh, 1vh) * 100); /* corrected viewport height using css custom variables */
}
```


## What problem this library solves
The viewport height which we use as "vh" unit in css does not gives actual viewport height but gives height of brwoser window.

![](https://res.cloudinary.com/css-tricks/image/upload/c_scale,w_1000,f_auto,q_auto/v1532099222/viewport-units-mobile-crop_gxa4yw.jpg)

## Installation
```shell
yarn add postcss-viewport-height-correction
# --- OR ----
npm install --save postcss-viewport-height-correction
```

And then add this javascript to `public/index.html` (for React), or add to `template.html` (for Preact).
```js
function setViewportProperty(){
    var vh = window.innerHeight * 0.01;
    document.documentElement.style.setProperty('--vh', vh + 'px');
}

window.addEventListener('resize', setViewportProperty);
setViewportProperty(); // Call the fuction for initialisation
```

[PostCSS]: https://github.com/postcss/postcss


Check you project for existed PostCSS config: `postcss.config.js`
in the project root, `"postcss"` section in `package.json`
or `postcss` in bundle config.

If you already use PostCSS, add the plugin to plugins list:

```diff
module.exports = {
  plugins: [
+   require('postcss-viewport-height-correction'),
    require('autoprefixer')
  ]
}
```

If you do not use PostCSS, add it according to [official docs]
and set this plugin in settings.

[official docs]: https://github.com/postcss/postcss#usage
