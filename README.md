# Jekyll default mockup setup

From now on we use Jekyll for our mockups as this supports both SASS and Github pages.

## Jekyll

[Jekyll](https://jekyllrb.com) is a simple, blog-aware, static site generator. It generates pages from html and markdown files and supports [SASS](http://sass-lang.com). It has it's own templating language called  [Liquid.](https://shopify.github.io/liquid/) [Github pages](https://pages.github.com) also supports Jekyll out of the box.

### Installation
Follow the guideline on the website.
- [Linux](https://jekyllrb.com/docs/installation/)
- [Windows](https://jekyllrb.com/docs/windows/#installation-via-rubyinstaller)
  - Problem with mingw32 can be solved with `bundle update && bundle install`

### Serving

```bash
bundle exec jekyll serve
```

Default port is 4000 so you can go to your page here [http://localhost:4000](http://localhost:4000). The finished site will be in the `_site` folder.

#### Build
If you just want to build the website without serving it:

```bash
bundle exec jekyll build
```
## Default index route

The base file for the whole application is called `home.html` and located in the `_layouts` folder. This will appear on the index route at [http://localhost:4000](http://localhost:4000).

## How to include html files

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

### Importing a sass file
If you don't want to include the head.html use the following in your desired html file. The file extension here has to be **.css**.
``` html
  <link rel="stylesheet" href="{{ site.baseurl }}/sass/desired.css">
```

## How to add new javascript file

In the `scripts` folder simply add a new js file. To include it modify the `_includes/js_files.html` or your desired html file like this:

``` html
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>

<script type="text/javascript" src="{{ site.baseurl }}/scripts/test.js"></script>
```

Example is in `test.js`.

## How to add a new subpage

Add a new html file in the `pages` folder. Example is in `pages/example.html`. It has to start like this:
``` html
---
permalink: /name-of-your-link
---

<!-- content of your html file-->
```

If you want it to have a default look, you can add the `_layouts/page.html` layout to it, that includes the header and the js files. Example is in `pages/example_with_layout.html`.
``` html
---
permalink: /name-of-your-link
layout: page
---
```
## How to use assets
### Image

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

### Custom font

Fonts are stored in the `assets/fonts` folder. Example for import is in `sass/font-icons.scss`
```css
@font-face {
	font-family: 'pmx';
	src:url('../assets/fonts/pmx.eot?8b80t1');
	src:url('../assets/fonts/pmx.eot?8b80t1#iefix') format('embedded-opentype'),
		url('../assets/fonts/pmx.ttf?8b80t1') format('truetype'),
		url('../assets/fonts/pmx.woff?8b80t1') format('woff'),
		url('../assets/fonts/pmx.svg?8b80t1#pmx') format('svg');
	font-weight: normal;
	font-style: normal;
}
```

Example usage is in `_layouts/home.html` and `sass/default.scss`.
```html
<i class="icon__account"></i>
```
```css
.icon__account:before {
  content: '\e074';
  font-family: 'pmx';
}
```
