Recognizr
=========

A small library to detect capabilities of mobile browsers.

What?
=====

Recognizr parses the browser UA (gosh!) to detect the capabilities of the browser. Capabilites are based on real-world testing across many browser platforms, rather than through feature detection.

One day, we won't need this library, as all browsers will support native overflow scrolling, smooth animations, and more. Until then, we have Recognizr. :)

Usage
=====

AMD:
```
define(['/path/to/recognizr'], function(Recognizr) {

  Recognizr.browser; // -> Returns current browser: split into family and version
  Recognizr.scroll;  // -> Returns scrolling capability.
  Recognizr.animations; // -> Returns whether CSS3 animations are supported or not.
  Recognizr.audio; // -> Returns whether the HTML5 audio element is supported or not.
  
});
```

Browser global:
```
(function(Recognizr) {

  // As above
  
})(window.Recognizr);
```

Properties
==========

### `browser`
Returns an object:
`{ 'family' : '{family}', 'version' : '{version}' }`
where:
- `{family}` is the browser family: one of *safari*, *chrome*, *android*, *firefox*, *msie*, *blackberry* or *unknown*
- `{version}` is an array which represents the version number of the browser or OS, separated by category from major to minor. For example, a for a device running iOS 5.1, the value would be ['5', '1'].

### `scroll`
Returns an object:
`{ 'toolbar' : '{toolbar}', 'form' : '{form}' }`
where:
- `{toolbar}` is one of `fixed` or `inline` depending on whether position:fixed is supported for anchoring the header/footer bars to the top and bottom of the screen.
- `{form}` is one of `fixed` or `inline` depending on whether the toolbars should be fixed when form elements are active. Most mobile browsers have issues when using position:fixed and form elements are active, so this field can be used to revert back to inline scrolling if needs be.

### `animations`
Theoretically, both iOS 4+ and Android 2.1+ support CSS3 animations, transforms and translates. In reality, performance on some platforms is poor. Use this property to determine whether you should support animations (`true` / `false`).

### `audio`
Use this property to determine whether you should support audio (`true` / `false`). Support for the HTML5 audio element and its API is poor on some platforms.

Contributions
=============

Many thanks to @jtward for his tireless help.

License
=======

Do what you like. :)
