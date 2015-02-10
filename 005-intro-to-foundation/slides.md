<aside class="notes"></aside>
# Introduction to Foundation Framework

## 2014-09-24



<aside class="notes"></aside>
# What is Foundation?



## What is Foundation?
<aside class="notes"></aside>

* A frontend framework
* Developed by Zurb
* First release in 2011
* Sass based
* Responsive & Mobile first



## The Grid System
<aside class="notes"></aside>

### Responsive

* Default size definition (media queries)
  * small (default)
  ```css
  @media only screen { } /* Define mobile styles */
  ```
  * medium
  ```css
  @media only screen and (min-width: 40.063em) { } /* min-width 641px */
  ```
  * large
  ```css
  @media only screen and (min-width: 64.063em) { } /* min-width 1025px */
  ```
  * xlarge
  ```css
  @media only screen and (min-width: 90.063em) { } /* min-width 1441px */
  ```
* The above keywords are useful for making or HTML semantic



## The Grid System
<aside class="notes"></aside>

### There are also other useful keywords

xxlarge
```css
@media only screen and (min-width: 120.063em) { } /* min-width 1921px */
```

landscape
```css
@media only screen and (orientation: landscape) { }
```

portrait
```css
@media only screen and (orientation: portrait) { }
```

retina
```css
@media only screen and (-webkit-min-device-pixel-ratio: 2),
@media only screen and (min--moz-device-pixel-ratio: 2),
@media only screen and (-o-min-device-pixel-ratio: 2/1),
@media only screen and (min-device-pixel-ratio: 2),
@media only screen and (min-resolution: 192dpi),
@media only screen and (min-resolution: 2dppx) { }
```



## The Grid System
<aside class="notes"></aside>

### 12 columns nestable grid

Let's try it out!

```
<div class="row">
  <div class="large-4 columns">Col A</div>
  <div class="large-4 columns">Col B</div>
  <div class="large-4 columns">Col C</div>
</div>
```



## The Grid System
<aside class="notes"></aside>

### Make it responsive!

```
<div class="row">
  <div class="small-9 medium-1 large-4 columns">Col A</div>
  <div class="small-2 medium-2 large-4 columns">Col B</div>
  <div class="small-1 medium-9 large-4 columns">Col C</div>
</div>
```



## The Grid System
<aside class="notes"></aside>

### Center, Push, Pull and Offset

For example:

* `large-centered`
* `large-pull-1`
* `large-push-2`
* `large-offset-3`

```
<div class="row">
  <div class="large-12 columns">
    Let's make some trials here!
  </div>
</div>
```    



## The Grid System
<aside class="notes"></aside>

### Nestable

```
<div class="row">
  <div class="large-6 columns">
    <div class="row">
      <div class="large-6 columns">Col A</div>
      <div class="large-6 columns">Col B</div>
    </div>
  </div>
  <div class="large-6 columns">Col C</div>
</div>
```



## The Block Grid 
<aside class="notes"></aside>

Evenly distribute your elements

```
<ul class="small-block-grid-2 medium-block-grid-3 large-block-grid-4">
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
  <li>Item 4</li>
  <li>Item 5</li>
  <li>Item 6</li>
</ul>
```



## Visibility
<aside class="notes"></aside>

```html
<div class="row bg-colored">
  <div class="show-for-small-only">Col A</div>
  <div class="show-for-medium-up">Col B</div>
  <div class="hide-for-large-only">Col C</div>
</div>
```



## Interchange
<aside class="notes"></aside>

Dynamically load content for different screen size

```html
<div class="row">
  <div data-interchange="[./interchange/small.html, (small)], [./interchange/medium.html, (medium)], [./interchange/large.html, (large)]">
    default
  </div>
</div>
```



## Interchange
<aside class="notes"></aside>

Pick optimal image for different devices

```html
<div class="row">
  <img data-interchange="[./img/puppy-1.jpg, (small)], [./img/puppy-2.jpg, (medium)], [./img/puppy-3.jpg, (large)]">
  <noscript><img src="./img/puppy-1.jpg"></noscript>
</div>
```

Interchange also works for background-image



## Really handy built-in CSS classes
<aside class="notes"></aside>

* `.clearfix`
* `.left, .right`
* `.radius .round`
* `.text-right, .text-justify`
* `.small-text-left, .large-only-text-center`



## Image thumbnails with responsive lightbox
<aside class="notes"></aside>

```html
<div class="row">
  <ul class="clearing-thumbs small-block-grid-3" data-clearing>
    <li><a class="th" href="./img/puppy-1.jpg"><img src="./img/puppy-1.jpg"></a></li>
    <li><a class="th" href="./img/puppy-2.jpg"><img src="./img/puppy-2.jpg"></a></li>
    <li><a class="th" href="./img/puppy-3.jpg"><img src="./img/puppy-3.jpg"></a></li>
  </ul>
</div>
```



<aside class="notes"></aside>
# Let's move on to see some cool Javascript features!



## Navigation
<aside class="notes"></aside>

Offcanvas is one of the navigation menus provided by Foundation.



## Create a Offcanvas menu
<aside class="notes"></aside>

```html
<div class="off-canvas-wrap" data-offcanvas>
  <div class="inner-wrap">

    <a class="left-off-canvas-toggle" href="#" >Menu</a>

    <!-- Off Canvas Menu -->
    <aside class="left-off-canvas-menu">
        <!-- whatever you want goes here -->
        <ul>
          <li><a href="#">Item 1</a></li>
        ...
        </ul>
    </aside>

    <!-- main content goes here -->
    <p>Set in the year 0 F.E. ("Foundation Era"), The Psychohistorians opens on Trantor, the capital of the 12,000-year-old Galactic Empire. Though the empire appears stable and powerful, it is slowly decaying in ways that parallel the decline of the Western Roman Empire. Hari Seldon, a mathematician and psychologist, has developed psychohistory, a new field of science and psychology that equates all possibilities in large societies to mathematics, allowing for the prediction of future events.</p>

  <!-- close the off-canvas menu -->
  <a class="exit-off-canvas"></a>

  </div>
</div>
```



## Form Validation
<aside class="notes"></aside>

Foundation has include abide.js for HTML form validation

```html
<div class="row">
  <form data-abide>
    <div class="name-field">
      <label>Your name <small>required</small>
        <input type="text" required pattern="[a-zA-Z]+">
      </label>
      <small class="error">Something is wrong</small>
    </div>
    <div class="email-field">
      <label>Email <small>required</small>
        <input type="email" required>
      </label>
      <small class="error">Something is wrong.</small>
    </div>
    <button type="submit">Submit</button>
  </form>
</div>
```



<aside class="notes"></aside>
# Foundation is what we need? 



## Let's compare with Bootstrap
<aside class="notes"></aside>

* Foundation
  * Mobile first
  * Relative sizing unit
  * Easier Customization

* Bootstrap
  * Larger community
  * More themes
  * Support IE8



![fullscreen](assets/images/wines.jpg)



## References
<aside class="notes"></aside>

* [Nick Pettit - Should You Use Bootstrap or Foundation?](http://blog.teamtreehouse.com/use-bootstrap-or-foundation)
* [Chris Sevilleja - Foundation 5 Features that Bootstrap Doesn’t Have](http://scotch.io/tutorials/css/foundation-5-features-that-bootstrap-doesnt-have)
* [Marc Schenker - Bootstrap vs. Foundation: Which Framework is Better?](http://bootstrapbay.com/blog/bootstrap-vs-foundation/)
