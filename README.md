# anims

css foundation for build and loop animations.  

## Basic usage:

Add the `move` class and an animation class to animate an element in. Override timing and animation defaults in CSS, or inline via the style attribute.

Here is a paragraph animating into view, vertically from below for 1 second:
```html
<p class="move moveY" style="--distance: 100%; --duration: 1s">...</p>
 ```

By default, all animations start by fading in from 0 opacity to 1. Even looping or repeating animations will fade in when they start. This effect works well for build animations that introduce an element on the page. 
If you don't want the element to fade in, set `--fadeDuration: 0;` on it via CSS.

## animation classes:
- `moveX`: move vertically (100% of element width is default distance. Override with `--distance` var)
- `moveY`: move vertically (100% of element height is default distance. Override with `--distance` var)
- `moveRotate`: rotate element from center. Positive numbers are clockwise. (15deg is default rotation. Override with `--rotation` var)

Note: The transform origin is `transform-origin: 50% 50%;`, the center point, for rotations, but if you're animating svg elements, that center point refers to the center of the whole svg rather than the element itself. You can set `transform-origin` to a location in the svg graphic where you need it to accommodate this difference.

## options available to set via css on the element (default values shown):

```css
--duration: 1s; /* duration of the move or rotate animation */
--delay: 0; /* delay before all animations begin */
--easing: ease-in-out; /* easing to use for the move or rotate animation */
--fadeDuration: 2s; /* duration of the fade-in */
--fadeDelay: var(--delay); / duration of the  */
--iteration: 1; /* how many times the move or rotate animation should run. if it's infinite, use a repeat class below */
--direction: alternate; /* when repeating, should it go back and forth or "normal". if infinite, use a repeat class below */ 
```

## animation repeat classes:
- `moveRepeat`: repeat animation infinitely from the start (good for spinning)
- `moveLoop`: repeat animation infinitely back and forth (good for pendulum)

## examples

more here https://codepen.io/anon/pen/MZLoQa?editors=1000 

paragraph sliding back and forth 25px horizontally:
```html
<p class="move moveX moveLoop" style="--distance: 25px; --duration: 1s">...</p>
 ```
 
div rotating endlessly:
```html
<p class="move moveRotate moveRepeat" style="--rotation: 360deg; transform-origin: 50% 50%; --duration: 4s">...</p>
 ```


svg rotating back and forth infinitely:
```svg
<g class="move moveRotate moveLoop" style="--rotation: 10deg; --duration: 20s; --delay: 10s">...
 ```
