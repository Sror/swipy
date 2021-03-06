Swipy.js
========

Forward / back swiping, smooth CSS3 transitions and even iOS 7 style parallax for your iOS web app and responsive website.


### The recipe ###

* [Modernizr](http://modernizr.com/download/#-applicationcache-inputtypes-touch-shiv-mq-cssclasses-teststyles-prefixes-load)
* [jquery.transit](http://ricostacruz.com/jquery.transit/)
* [Hammer.js](https://github.com/EightMedia/hammer.js)
* [Waypoints.js](https://github.com/Skookum/waypoints) (not the one for scrolling)
* [FontAwesome](http://fortawesome.github.io/Font-Awesome/)


### Installation ###

1. The first ingredient is Modernizr with yepnope. If you already have it included then you're covered. You need <code>touch</code> and <code>load</code>. Otherwise include <code>lib/modernizr.custom.js</code>

  ```html
  <script type="text/javascript" src="/scripts/swipy/lib/modernizr.custom.js"></script>
  ```

2. Include Swipy.js

  ```html
  <script type="text/javascript" src="/scripts/swipy/swipy.min.js"></script>
  ```

3. Swipe away

  ```javascript
    Swipy.swipe({
      master: 'html',
      page: 'body',
      path: {
        swipylib: '/scripts/swipy/lib'
      },
      showtouches: true,
      forceshowtouches: true,
      debug: true
    });
  ```


### Options ###
```javascript
Swipy.defaults = {
  master: 'html',
  page: 'body',
  path: {
    swipylib: '/scripts/swipy/lib',
    css: true, // '/scripts/swipy/lib/swipy.css',
    hammer: true, // '/scripts/swipy/lib/jquery.hammer.min.js',
    showtouches: true, // '/scripts/swipy/lib/hammer.showtouches.min.js',
    transit: true, // '/scripts/swipy/lib/jquery.transit.min.js',
    waypoints: true, // '/scripts/swipy/lib/waypoints.min.js',
    appcache: '/appcache.manifest'
  },
  speed: 200, // speed of animations
  scale: 0.85, // scale of page during dragging
  drag_timeout: 3000, // in ms, cancels page switch if drag is more than that
  drag_distance: 0.5, // drag at least half the width of master to trigger page switch
  drag_min_distance: 20, // in px, Hammer.js option to trigger drag
  drag_min_deltaTime: 20, // in ms, cancels page switch if drag is less than that
  edge_buffer: 10, // in px, drag doesn't kick in before drag_min_distance of the edge so we need a "grab" buffer (could be drag_min_distance * 2)
  intercept: 'a', // web app mode only, we need all links and then exclude a lot
  ignore: 'a[rel=external], a[rel=nofollow], a[href$=".pdf"], a[id^=fancybox]', // example exclude list, needs updating because of iOS 7
  swipynav: true,
  swiypynav_prependto: 'body',
  showtouches: false, // desktop demo
  forceshowtouches: false,
  overflowHTML: false,
  velocity: false, // experimental
  velocity_trigger: 0.65,
  webkitsticky: false, // experimental
  appcache: false, // experimental
  parallax: false, // experimental
  parallax_distance: 150,
  parallax_offset: 50,
  parallax_throttle: 50, // in ms
  debug: false, // pardon this vichyssoise of verbiage that veers most verbose
  debug_parallax: false
};
```


### CSS ###

Swipy includes it's own CSS when launched, if you prefer loading it before or throwing it in your compressor go ahead. Just set <code>options.path.css</code> to <code>false</code>. You should also be able to style this as you like. Swipy includes a navigation bar that uses FontAwesome icons, make sure you add that for full awesomeness out of the box.

```html
<link type="text/css" rel="stylesheet" media="all" href="/scripts/swipy/swipy.css" />
```