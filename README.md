Recognizr
=========

A small library to detect capabilities of mobile browsers.

Include
=======

### AMD

You can require this in the regular way. See the RequireJS API for more details.

### Browser global

If you don't want to use AMD, Recognizr will be available as `window.Recognizr`.

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
}
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
A fixed header and/or footer is a staple for native mobile apps. The mobile web is not so forgiving. Som,e browsers support native fixed toolbars with support for CSS `overflow: scroll`, others need to use iScroll, and some can't use either and must fallback to inline header/footers.

This property indicates which you should use for this browser. Possible values are:
- *positionfixed* - you can use the `position: fixed` CSS property on the fixed header, and the `overflow: scroll` CSS property on the scrolling body.
- *overflowscroll* - you should absolutely position the header/footer with respect to the body using the `position: absolute` CSS property and provide native scrolling in the content region with `overflow: scroll`.
- *polyfillscroll* - you will need to polyfill the scrolling, using something such as iScroll.
- *inline* - you shpould let the browser take care of scrolling the entire document as one. You probably have an old browser.

### `animations`
Theoretically, both iOS 4+ and Android 2.1+ support CSS3 animations, transforms and translates. In reality, performance on some platforms is poor. Use this property to determine whether you should support animations (`true` / `false`).

License
=======

Do what you like. :)
