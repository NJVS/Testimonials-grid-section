# Frontend Mentor - Testimonials grid section solution

This is a solution to the [Testimonials grid section challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/testimonials-grid-section-Nnw6J7Un7). Frontend Mentor challenges help you improve your coding skills by building realistic projects. 

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
  - [Useful resources](#useful-resources)


## Overview

### The challenge

Users should be able to:

- View the optimal layout for the site depending on their device's screen size

### Screenshot

![](./design/ssdesktop.png)
![](./design/sstablet.png) ![](./design/ssmobile.png)

### Links

- [Live Demo](https://njvs.github.io/Testimonials-grid-section/)

## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties
- [SASS/SCSS](https://sass-lang.com) - CSS with superpower
- Flexbox
- CSS Grid
- Responsive Web Design

### What I learned

I use CSS Grid (grid-template-areas) on desktop and CSS Flexbox for mobile view.
```scss
main.container {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-gap: 1.5em 2.3em;
  grid-template-areas:
    "c1 c1 c2 c5"
    "c3 c4 c4 c5";
  @media (max-width: 426px) {
    display: flex;
    flex-direction: column;
  }
}
```

For the background color for each card, I decided to just assign a class for each background color...
```html
<div class="card card-bg-violet">...</div>
<div class="card card-bg-grayblue">...</div>
<div class="card card-bg-white">...</div>
<div class="card card-bg-blackblue">...</div>
<div class="card card-bg-white">...</div>
```
...And use SCSS `@each` and `@if` rules to dinamically style each of its background color and font color. There is also a profile picture border color that is only applied to `.card-bg-violet` and `.card-bg-blackblue`.
```scss
.card {
  @each $-color, $-value in var.$card-bg-color {
    &-bg-#{$-color} {
      background-color: $-value;

      color: if(
        index('white', $-color),
        map-get(var.$card-bg-color, 'blackblue'),
        var.$color-grayish-blue
      ) !important;

      .card-header .card-header-img {
        border: 2px;
        border-style: solid;
        border-color: if(index(('violet', 'blackblue'), $-color), #A775F1, transparent);
      }
    }
  }
}
```

### Useful resources

- [A Complete Guide to Grid](https://css-tricks.com/snippets/css/complete-guide-grid/) - I alway open this guide every time I use CSS Grid
- [A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/) - This is for CSS Flexbox
- [SASS @each rule](https://sass-lang.com/documentation/at-rules/control/each)
- [SASS @if and @else rule](https://sass-lang.com/documentation/at-rules/control/if)