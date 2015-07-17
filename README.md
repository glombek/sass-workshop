Let's make this more... Sassy!
====================================

<img src="https://github.com/glombek/sass-workshop/blob/master/resources/sass.gif?raw=true" alt="Sass" />

0. ###Variables

  The first feature we're covering of Sass is variables. Pretty much anything that can be a CSS property value can be a Sass variable. Examples include `color`s,  `font-famil[ie]`s and size values (eg `10px`).
  
  The example code has a few ideal candidates for variables.
  
  **Create some variables for the reused colours and font families.**
 
0. ###Nesting

   There's a lot of repetition going on here. Let's fix that.
   
   See how we want to style the `h1` inside the `article`? At the moment we have to write the following:
   
   ```
   article {
    /* styles for article */
   }
   
   article h1 {
    /* styles for h1 */
   }
   ```
   
   but in Sass, we can *nest* to save typing and improve readability:
   
   ```
  	article {
		/* styles for article */
		
		h1 {
			/* styles for h1 */
		}  
	}
   ```
   
   It outputs exactly the same CSS, but it's much easier to read, don't you think?
   
   **Nest the `article *` styles in the demo. **
   
   **WARNING:** When it comes to nesting, don't go too overboard! Only nest where you need to. Nesting can encourage you to create overly specific selectors (which are hard to overwrite) and can create very long chains which are slower for a browser to decode. 
   
0. ###Nesting properties

  As well as nesting selectors, we can nest properies! This can hugely improve readability in place of shorthand properties or provide shortcuts for properties that aren't available in shorthands previously!
  
  Example crazy CSS shorthand:
  
  ```font:italic small-caps bold 1em/140% "Lucida Grande",sans-serif;```
  
  What it's short for:
  
  ```
  font-style: italic;
  font-variant: small-caps;
  font-weight: bold;
  font-size: 1em;
  line-height: 140%;
  font-family: "Lucida Grande",sans-serif;
  ```
  
  But with a little Sass...
  
  ```
  font: { 
    style: italic;
    variant: small-caps;
    weight: bold;
    size: 1em;
    height: 140%;
    family: "Lucida Grande",sans-serif;
  }
  ```
  
  It forms a bit more of a happy medium!
  
  **Nest some of the text-\* properites to simplify things.**

0. ###Parent selector

  In the earlier nesting task we couldn't nest the styles for `a` because the further selectors `.btn` and `:hover` are not targetting *children* of the `a` but variations upon itself.
  
  Fortunately, Sass provides us with the parent selector, the ampersand (`&`). It can be used to grab the current selector and choose where to place it. For example:
  
  ```
    input {
      /* my input styles */
      &:hover {
        /* styles for when input has the hover state */
      }
    }
  ``` 
  
  We can also use this to prepend styles in special cases:
  
  ```
    .sub-menu {
      display: none;
      
      .menu-item:hover & {
        display: block;
      }
    }
  ```
  
  **The styles for `a` could utilise nesting with use of the parent selector function. Try it.**

  ####UGLY CSS WARNING!
  Nesting makes it very easy to build up long selectors! This makes things very specific - its hard to override and is slower for browsers to decode. Only use it if you need to!

0. ###Operators
  We can also use `+`, `-`, `/`, `*` and `%` in Sass to help calculate our values.
  
  Say we've been using media queries with `min-width: $myCutoff` (note the use of a variable here) but for some reason we want to do a one-off `max-width`:
   
   ```
   @media (max-width: $myCutoff + 1px) { ... }
   ```
   
    We'll use operators in our demo once we've covered the next section.
  
0. ###Mixins
  Mixins are Sass's answer to functions.
  
  You'll notice in the demo, we're using `rem` values instead of `px` (Yay! Good practice! Down with pixes!). However, this demo site needs to have a fallback in place for legacy browsers. This means in CSS, we'd be putting our values in as `rem` then manually multiplying the result by `16` to get the `px` value.
  
  When we come to Sass, this is a clear case for operators:
  
  ```
  font-size: 2 * 16px;
  font-size: 2rem;
  ```
  
  But this isn't ideal. We're still repeating the values `2` (for this value) and `16` (each time we calculate it). So, we'll create a function:
  
  ```
  @mixin rem($property, $values...) {
  $max: length($values);
  $pxValues: '';
  $remValues: '';

  @for $i from 1 through $max {
    $value: nth($values, $i);
    $pxValues: #{$pxValues + $value*16}px;

    @if $i < $max {
      $pxValues: #{$pxValues + " "};
    }
  } 

  @for $i from 1 through $max {
    $value: nth($values, $i);
    $remValues: #{$remValues + $value}rem;

    @if $i < $max {
      $remValues: #{$remValues + " "};
    }
  } 
  
  #{$property}: $pxValues; 
  #{$property}: $remValues; 
}
  ```
  
  Notice how we can use `if` and looping logic!
  
  Then we can use this function like so:
  
  ```
  @include rem(font-size, 2);
  
  /* We can also pass in multiple values */
  @include rem(margin, 2, 1, 2, 1);
  ```
  
  **Copy this mixin into the SCSS file and use where we have an `rem` value with `px` fallback. **
  
0. ###Partials and Importing
0. ###Bourbon and Compass
0. ###Comments
0. ###Extend (inheritance)

**We're done!**

<img src="https://github.com/glombek/sass-workshop/blob/master/resources/happydance.gif?raw=true" alt="Happy dance" title="Happy dance" /> *


\* Orange is the New Black is cool, OK?\*\*

\*\* The GIFs and (lack of) colour scheme were explicitly added to make Ben feel at home.
   
