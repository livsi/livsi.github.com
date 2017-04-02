## Site

https://livsi.github.io

## Cards Jekyll Template

Features:

- Gulp
- Stylus (Jeet, Rupture, Kouto Swiss)
- Live Search
- Offcanvas Menu
- SVG icons
- Very very small and fast!
- Shell Script to create posts
- Tags page
- Series page
- About Me page
- Feed RSS
- Sitemap.xml
- Color Customization
- Info Customization

## Color customization

All color variables are in [src/styl/_variables.styl](src/styl/_variables.styl). To change the main color, just set the new value at `main` assignment. Another colors are for texts and the code background color.

## Theme Colors

Every post has a main color that is defined on [src/styl/_theme-colors.styl](src/styl/_theme-colors.styl). Just create a new color with the prefix `post-` and define your main-class: 'css' and color: '#2DA0C3' on every post you create.

## Creating posts

Use the `initpost.sh` to create your new posts. Just follow the command:

```
./initpost.sh -c Post Title
```
