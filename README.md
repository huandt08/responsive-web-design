# **Responsive Web Design Learning**
***
## 1. Essential of Responsive 
## 2. Media queries
## 3. Fuild layout and responsive image

### Flexbox alignment properties
two axis: main axis and cross axis

if flow-direction = row, main axis is horizontal axis, cross axis is vertical axis
if flow-direction = colunm, main axis is vertical axis, cross axis is horizontal axis

### Possible alignment values
- flex-start: begin at the starting edge of its flex container
- flex-end: at the end of the flex container
- center: Puts it in the middle of the flex container
- baseline: Sets all flex items in the container so that their baselines align
- stretch: Makes the items stretch to the size of their flex container (in the cross axis)

### The justify-content property
- Controll in main axis: justify-content and justify-self
- Possible values:
  - flex-start
  - flex-end
  - center
  - space-between
  - space-around

### The flex property
flex: grow shrink basic

### Simple sticky footer
Use flex: 1 to put footer on the bottom of the page

### Changing source order
Use order: <number> and media queries to re-ordering web structure

## Responsive Images
### The intrinsic problem of responsive images
Need to tell browser which images is the most appropriate?

### Simple resolution switching with srcset
srcset provide list of images that browser can choose. Base on resolution of the screen
But how about size of image

### Advanced switching with srcset and sizes
```html
<img srcset="scones-small.jpg 450w, scones-medium.jpg 900w" sizes="(min-width: 17em) 100vw, (min-width: 40em) 50vw" src="scones-small" alt="Scones">
```
- When device has width larger then 17em, image will pretenting to used in 100vw wide, if device has at least 40em wide, then image intend to be shown at 50vw
- On 320px wide device with 2x resolution. => requires image with 320 x 2 = 640px wide.
And browser might decide to use 900w image wide - scones-medium.jpg

### Did you say the browser 'might' pick one image over another?
- *sizes* attributes are merely hints, can not ensure browser will always obey. Relate to ascertain network conditions.
- User can setting their device to only download 1x iamge or only download 2x image.
- Alternative to the browser deciding is use the *picture* element.

### Art direction with the picture element
```html
<picture>
  <source media="(min-width: 30em)" srcset="cake-table.jpg">
  <source media="(min-width: 60em)" srcset="cake-shop.jpg">
  <img src="scones.jpg" alt="One way or another, you WILL get cake.">
</picture>
```
- *picture* is wrapper
- style image by *img* tag
- srcset works exactly the same as previous example
- *img* provide fallback image
- Key different is *source* tag. tell browser which image is need to load.

### Facilitate new-fangled image formats
**WEBP**
```html
<picture>
  <source type="image/webp" srcset="scones-baby-yeah.webp">
  <img src="scones-baby-yeah.jpg" alt="Again, you WILL eat cake.">
</picture>

```