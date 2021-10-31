# accessible

## role + tabindex

- tabindex indicates the element can receives focus
- to remove tabindex, add `-1` instead of `0`
- just add with elements that can be selected
- role makes a tag behaves like other one that it's more accessible

```html
<a role="button" tabindex="0">name of button</a>
```

## colors

- design in gray scale -> gray scale chrome plugin
- high contrast -> use a color contrast checker
- not rely solely on red for error -> add icons
- not rely solely on color swatch -> name the color
- hover -> use color change and border (both)

## aria attributes

- aria label = `aria-`

1. `aria-expanded`
- for mobile menus
- set to false
- then when the user clicks, use js to set it to true

2. `aria-label`
- when you have icon inside links `<a></a>`
- example: `aria-label="follow company on instagram"` when you have the instagram icon with no text
- or you can hide the icon using `aria-hidden="true"` if the icon is just decoration

3. `aria-labelledby`
- when you have `<img>`, instead of use just `alt`
- if you have a caption, use the `id` of the caption on this aria
- example: `aria-labelledby="captionId"`

4. `alt`
- describe the image
- always use `alt`
- if you gonna use it as a link, say its a link to somewhere
- if you have the `aria-labelledby`, keep the `alt` there, but empty `alt=""`

5. `aria-current="page"` 
- use to highlight the page you are
- announces the page you are

```css
nav ul li a[aria-current="page"]{
    font-weight: bold;
    border-bottom: 1px solid red;
}
```

## outline

- don't remove it!
- it shows each element is selected
- create a custom outline
- use a color that is different from the colors of your site

```css
*:focus {
    outline: 4px solid red;
}
```

- use the same css effects you use on `: hover`

```css
button:hover, button:focus {
    color: white;
    background-color: blue;
    border-color: blue;
}
```

## bypass block

- skip links that are not main actions
- it only appears if you use tab navigation

```html
<div class="skip">
    <a href="#content">Skip to main content</a>
</div>

<main id="content"></main>
```

```css
.skip a {
    // make it invisible
    position: absolute;
    left: 100000000px;
    top: auto;
    width: 1px;
    height: 1px;
    overflow: hidden;
    font-size: 2em;
    background: white;
    font-weight: bold;
    display: block;
    padding: 10px;
}

.skip a:focus {
    // it is visible if you press tab
    position: static;
    width: auto;
    height: auto;
    border: 1px solid red;
}
```

## hamburguer menu

- use the `aria-expanded` via js

## forms

- always use `<label></label>`
- you can place the `<input>` inside the label
- if you place it outside, it needs to add `for="name"` in the label and `id="name"` in the input

```html
<label> 
    Name
    <input
        type="text"
        class="form-control"
    >
</label>
```

- style the * if required 
- provide instructions for the * (what * means?)
- use `aria-hidden` to hide the * because the input will say it's required
- uses `required` in the input
- uses `aria-required="true"` if you can't use the `required` html5
- focus with outline in each input
- don't use placeholder

```html
<label for="name">Name 
    <span 
        style="color="red"
        aria-hidden="true"
    >*</span>
</label>
<input
    id="name"
    type="text"
    class="form-control"
    required
>

```

## links 

- open new window is not accessible!
- but if you need it...
- include `rel="noopener"` inside `<a></a>`
- add an icon (svg) that shows it opens on a new window
- hide the icon from screen readers using `aria-hidden="true"`
- add `aria-label="site x opens in a new window"`
- use decoration to show it's a link (underline and different color)
- never use "click here" -> describe the text





