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
- `{family}` is the browser family: one of *safari*, *chrome*, *android*, *msie*, *blackberry* or *unknown*
- `{version}` is a string representation of the version number of the browser. This corresponds to the OS version number (e.g. `'5'` for iOS 5)

### `scroll`
Returns an object:
`{ 'toolbar' : '{toolbar}', 'form' : '{form}' }`
where:
- `{toolbar}` is one of `fixed` or `inline` depending on whether position:fixed is supported for anchoring the header/footer bars to the top and bottom of the screen.
- `{form}` is one of `fixed` or `inline` depending on whether the toolbars should be fixed when form elements are active. Most mobile browsers have issues when using position:fixed and form elements are active, so this field can be used to revert back to inline scrolling if needs be.

### `animations`
Theoretically, both iOS 4+ and Android 2.1+ support CSS3 animations, transforms and translates. In reality, performance on some platforms is poor. Use this property to determine whether you should support animations (`true` / `false`).

Contributions
=============

Many thanks to @jtward for his tireless help.

License
=======

Do what you like. :)
