# Jekyll default mockup setup

From now on we use Jekyll for our mockups as this supports both SASS and Github pages.

The base file for the whole application is called `home.html` and located in the `_layouts` folder.

## How to install Jekyll

Follow the guideline on the website.
- [Linux](https://jekyllrb.com/docs/installation/)
- [Windows](https://jekyllrb.com/docs/windows/#installation-via-rubyinstaller)
  - Problem with mingw32 can be solved with `bundle update && bundle install`

To read on Liquid check [their website.](https://shopify.github.io/liquid/)

## How to include new html files

Create your html files in the `_includes` folder; You can include them in an .html file with the following command:

``` html
  {% include name.html %}
```

I've already created a default `head.html` and `js_files.html`.

## How to add a new sass file:

In the `sass` folder simply add a new `name.scss`. For Jekyll it is **important** to start the file like this:
``` sass
---
---

/*your sass code*/
```

Then you can include it in your `main.scss` with **css** suffix, as the preprocessort creates css from it.

``` sass
---
---

// the imported name has to be a .css file!
@import "default.css";
```

## How to add new javascript file

In the `scripts` folder simply add a new js file. To include it, modify the `_includes/js_files.html`, like this:

``` html
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>

<script type="text/javascript" src="{{ site.baseurl }}/scripts/test.js"></script>
```

Example is in `test.js`.

## How to add a new subpage

Add a new html file in the `pages` folder. Example is in `pages/example.html`. It has to start like this:
```
---
permalink: /name-of-your-link
---

<!-- content of your html file-->
```

If you want it to have a default look, you can add the `_layouts/page.html` layout to it, that includes the header and the js files. Example is in `pages/example_with_layout.html`.
```
---
permalink: /name-of-your-link
layout: page
---
```

## How to add an image

Images are stored in the `assets/images` folder. Adding them with inline html:

``` html
<img src="{{ '/assets/images/files.jpg' | relative_url}}"/>
```

Adding them via sass:
``` html
<div class="cover"></div>
```
```css
.cover {
  background-image:url('../assets/images/roadwork.jpg');
  height: 100px;
}
```

Examples are in `_layouts/home.html` and `sass/image.scss`.
