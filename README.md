Let's make this file more... Sassy!
====================================

<img src="https://mygymlessfitness.files.wordpress.com/2015/04/giphy-14.gif" alt="Sass" />

0. Variables
0. Nesting

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
   
   **Where can you implement nesting in the demo?**
   
   **WARNING:** When it comes to nesting, don't go too overboard! Only nest where you need to. Nesting can encourage you to create overly specific selectors (which are hard to overwrite) and can create very long chains which are slower for a browser to decode. 
   
0. Nesting properties
0. Parent selector
0. Operators
0. Mixins
0. Partials and Importing
0. Bourbon and Compass
0. Comments
0. Extend (inheritance)

**We're done!**
<img src="https://juliavanvalkenburg.files.wordpress.com/2015/06/post-28907-milkshake-scene-dancing-gif-al-w1lp.gif" alt="Happy dance" title="Happy dance" /> *




* Orange is the New Black is cool, OK?
   
