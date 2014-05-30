This document outlines the various guidelines and conventions you should adhere to when writing stylesheets.

If you have not already done so, you should first familarize yourself with and have an understanding of [Stylus](http://learnboost.github.com/stylus/) and the [Nib](http://visionmedia.github.com/nib/) library.

Coding Style
------------
* Use soft-tabs; two space indent. Please configure your text editor to use spaces instead of tabs.
* Put spaces after `:` in property declarations.
* Put spaces after `{` in rule declarations, on the same line as the selector.
* Always use hex color codes; Stylus even allows for `rgba(#fff, 50%)`.
* Use 3 character hexadecimal notation where possible.
* Use `//` for comment blocks (instead of `/* */`).
* Do not use units after `0` values unless they are required.
* Document styles with [KSS](https://github.com/kneath/kss).

Stylus Style
------------
* Do not omit braces, colons, or semi-colons.
* Prefix variables with `$`.
* Separate words in variable names with hypens.
* Separate mixin and function arguments with a space.
* As a rule of thumb, don't nest further than 3 levels deep. If you find yourself going further, think about reorganizing your rules (either the specificity needed, or the layout of the nesting).
* Do not use vendor prefixed properties unless required (i.e. the property is non-standard). Allow Nib to take care of this for you.
* Use the standard mixin syntax with parentheses for all other mixins.

Naming Conventions
------------
* Separate words in class names with hypens; camelCase IDs.
* Use names that reflect the purpose of the element instead of names that are strictly presentational.
* Unless necessary, do not overqualify ID and class names with type selectors.

Examples
--------

Example of bad syntax:

```stylus
badBackground = white;

.badExample{
  sprite: icn-cart;
  background: badBackground;
  box-shadow:0px 0px 5px rgba(0,0,0,30%);
}
```

Example of good syntax:

```stylus
$good-background = #fff;

.good-example {
  sprite('icn-cart');
  background: $good-background;
  box-shadow: 0 0 5px rgba(#000, 30%);
}
```

File Organization
-----------------
The stylesheet file organization should follow something like this:

```plain
stylesheets
├── partials
│   ├── account.styl
│   ├── checkout.styl
│   └── …
├── main.styl
└── variables.styl
```

Font Sizes
----------
Use `rem` for `font-size`. Additionally, unit-less line-height is preferred because it does not inherit a percentage value of its parent element, but instead is based on a multiplier of the font-size.

```css
html {
  font-size: 62.5%;
}

p {
  font-size: 1.4rem; // = 14px
  line-height: 1.5;
}
```
