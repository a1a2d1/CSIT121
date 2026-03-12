# Lab 04 – Project Design and Requirements

## Overview

The purpose of this lab is to create a multi-page website that incorporates
images and CSS styling to enhance visual design. The site will demonstrate
common web graphic formats and the use of CSS for styling.

## Requirements

1. Find 3 images with 3 different image types (GIF, JPG, PNG, WebP, or SVG).
2. Each image gets its own web page with the following:
   - Description of the image.
   - Information on file type of the image.
   - Why the image was chosen.
   - Source of the image.

3. Every page should contain semantic HTMl tags, headings tags, and content.
4. There should be 1 CSS stylesheet that does the following:
   - Style the typography.
   - Include a CSS background image applied to all pages.

5. Credit and link (new tab) the source of all images.
6. Validate all HTML pages and stylesheets.

## Project Layout

```Ascii
lab04/
│
├── index.html
├── earth-axis.html
├── earth-from-space.html
├── earth-render.html
├── style.css
│
└── images/
    ├── earth-axis.gif
    ├── earth-from-space.jpg
    └── earth-render.png
```

## Pages

- index.html - entry point
- earth-axis.html
- earth-from-space.html
- earth-render.html

## Navigation

Navigation menu in header. Same header and navigation menu on all pages.

## Page Structure

Use semantic HTML.

### Shared Layout

```Pug
header
  h1 Image Showcase

  nav
    ul
      li index.html
      li earth-axis.html
      li earth-from-space.html
      li earth-render.html

main page specific content

footer copyright
```

### Image Pages

```Pug
main
  section
    article
      h2 Image Title
      img(src="")

      h3 Description
      p Short description of the image

      h3 Image File Type
      p Explanation of file type

      h3 Why this image was chosen
      p Reason for selecting image

      h3 Source
      p
        a(href="#") link to source
```

## Design Notes

### Layout

- Use semantic HTML tags.
- Navigation menu will be at the top of every page.
- Every page is accessible from every page.

### Typography

- Verdana, Arial, sans-serif - applied to all pages.

### Accessibility

Provide description of images using the alt attribute.

### Image Sources

- [Earth Spinning on Its Axis](https://commons.wikimedia.org/wiki/File:Earth%27s_Axis.gif)

- [Earth From Space](https://commons.wikimedia.org/wiki/File:Space_%28Unsplash%29.jpg)

- [Rendering of Earth](https://commons.wikimedia.org/wiki/File:Earth_Blender_render_4_transparent_background.png)

- [Background Space Image](https://pixabay.com/photos/milky-way-stars-night-sky-2695569/)

## References

- [How to Add Background Image with CSS](https://www.w3schools.com/css/css_background_image.asp)

- [Navigation Bar](https://www.w3schools.com/css/css_navbar_horizontal.asp)

- [Ascii Text Generator](https://www.text-tree-generator.com/)

- [CSS: Text-align](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/text-align)

- [CSS: Display](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/display)

- [CSS: Height](https://www.w3schools.com/css/css_dimension.asp)
