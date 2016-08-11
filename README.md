# Animate.js [![Build Status](https://travis-ci.org/jshjohnson/Animate.svg?branch=develop)](https://travis-ci.org/jshjohnson/Animate)

Trigger animations on elements when they are in view 👓.

[Demo](https://joshuajohnson.co.uk/Animate/)

## Setup
```html
<script src="/assets/js/dist/animate.js"></script>
<script>
    var animate = new Animate({
        target: '[data-animate]',
        animatedClass: 'js-animated',
        offset: 0.5,
        delay: 0,
        remove: true,
        scrolled: false,
        reverse: false,
        debug: false,
        onLoad: true,
        onScroll: true,
        onResize: false,
        callbackOnInit: function(){},
        callbackOnAnimate: function(element){
            console.log(element);
        }
    });
    animate.init();
</script>
```

## Installation
To install via NPM, run `npm install --save-dev animate.js` 

## Animating elements
##### `data-animate`

Default way of targeting an element to animate (no value required). This can be overridden to be a custom attribute or class.

##### `data-animation-classes`

Animations to be added to element when it is in view. To add multiple classes, seperate each class with a space (as you would normally).

### Optional element overrides
##### `data-animation-delay`

Overide the plugin `delay` option per element.

##### `data-animation-offset`

Override the plugin `offset` option per element.

##### `data-animation-remove`

Overide the plugin `removeAnimations` option per element.

##### `data-animation-reverse`

Overide the plugin `reverse` option per element.

#### Examples
```html
<div data-animate data-animation-classes="animated fadeIn"></div>
<div data-animate data-animation-classes="animated tada" data-animation-delay="1000"></div>
<div data-animate data-animation-classes="animated bounce" data-animation-offset="0.2"></div>
<div data-animate data-animation-classes="animated bounce" data-animation-remove="true"></div>
```

## Options
#### target
Type: `String` Default: `[data-animate]`

Element/s to target. Once this element is in view, add animations.

#### animatedClass
Type: `String` Default: `js-animated`

Class to be added to element once animation has completed.

#### offset
Type: `Number` Default: `0.5` (50%)

Percentage of element that needs to be in the viewport before the animation triggers.

####  delay
Type: `Number` Default: `0`

Milisecond delay before animation is added to element in view.

####  remove
Type: `Boolean` Default: `true`

Whether animation classes should removed when the animations complete.

####  reverse
Type: `Boolean` Default: `false`

Once the element has left the top of the viewport (by the same offset), remove the animations from element. When the element comes back into view, it will animate again.

####  scrolled
Type: `Boolean` Default: `false`

Animate any elements that a user has already scrolled past.

#### debug
Type: `Boolean` Default: `false`

Debugging information in console.

#### onLoad
Type: `Boolean` Default: `true`

Whether to fire on DOMContentLoaded.

#### onScroll
Type: `Boolean` Default: `true`

Whether to fire on scroll.

#### onResize
Type: `Boolean` Default: `false`

Whether to fire on resize.

#### callbackOnInit
Type: `Function` Default: `function(){}`

Function to run once Animate.js initialises 

#### callbackOnAnimate 
Type: `Function` Default: `function(el){}`

Function to run once animation has completed (pass parameter to access the animated element).

## Methods
#### init();
Initialises event listeners.
#### kill();
Kills event listeners and resets options.
#### render();
Adds/removes animations without the need for event listeners.

## Browser compatibility
Animate.js is supported in modern browsers from IE9 and above (i.e. browsers that support CSS animations). Due to discrepencies in support for `Element.classList`, I would recommend including the very good [classList polyfill](https://github.com/eligrey/classList.js/) before you include animate.js. I would also suggest using Modernizr to feature detect CSS animations/transitions and apply override styling for browsers that do not support those features.

Using SCSS, this may look like this:
```css
.animate {
    opacity: 0;
    .no-csstransitions &, .no-cssanimations &  {
        opacity: 1;
    }
}
```

## Development
To setup a local environment: clone this repo, navigate into it's directory in a terminal window and run the following command:
* ```npm install```

### Gulp tasks
* ```gulp dev```
* ```gulp test```
* ```gulp build```

## Contributions
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code using Gulp...bla bla bla

## License
MIT License 
