# Very simple jQuery (color) picker

Yet another jQuery picker, forked from [jQuery Simple Color Picker](https://github.com/tkrotoff/jquery-simplepicker).
This plugin is unobtrusive and integrates well with Twitter Bootstrap (it works just fine without).
The source code only requires jQuery and is about 200 lines of JavaScript and 100 lines of CSS.

See the [online demo](http://shadowhand.me/simplepicker/).

![simplecolorpicker-inline.png](http://img11.hostingpics.net/pics/75504320131025121603ColorpickerforjQuery.png)

![simplecolorpicker-picker.png](http://img11.hostingpics.net/pics/71709820131025122115ColorpickerforjQuery.png)

## How to use

By default, SimplePicker works as a a color picker. Create a HTML select:

```HTML
<select name="colorpicker">
  <option value="#7bd148">Green</option>
  <option value="#5484ed">Bold blue</option>
  <option value="#a4bdfc">Blue</option>
  <option value="#46d6db">Turquoise</option>
  <option value="#7ae7bf">Light green</option>
  <option value="#51b749">Bold green</option>
  <option value="#fbd75b">Yellow</option>
  <option value="#ffb878">Orange</option>
  <option value="#ff887c">Red</option>
  <option value="#dc2127">Bold red</option>
  <option value="#dbadff">Purple</option>
  <option value="#e1e1e1">Gray</option>
</select>
```

add the plugin files:

```HTML
<script src="//ajax.googleapis.com/ajax/libs/jquery/1.10.2/jquery.js"></script>
<script src="jquery.simplepicker.js"></script>

<link rel="stylesheet" href="jquery.simplepicker.css">
```

then call the plugin:

```JavaScript
$('select[name="colorpicker"]').simplepicker();
$('select[name="colorpicker"]').simplepicker('selectOption', '#7bd148');
$('select[name="colorpicker"]').simplepicker('destroy');
```

and pass some options if needed:

```JavaScript
$('select[name="colorpicker"]').simplepicker({
  picker: true
}).on('change', function() {
  $(document.body).css('background-color', $('select[name="colorpicker"]').val());
});
```

### Options

- theme: font to use for the ok/check mark (default: `''`), available themes: [`regularfont`](https://github.com/ushahidi/jquery-simplepicker/blob/master/jquery.simplepicker-regularfont.css), [`fontawesome`](https://github.com/ushahidi/jquery-simplepicker/blob/master/jquery.simplepicker-fontawesome.css), [`glyphicons`](https://github.com/ushahidi/jquery-simplepicker/blob/master/jquery.simplepicker-glyphicons.css)
- picker: show the colors inside a picker instead of inline (default: `false`)
- pickerDelay: show and hide animation delay in milliseconds (default: `0`)
- setIconValue: callback to update the HTML of the picker icon for a value (default: `function($icon, value){ $icon.css('background-color', value).addClass('empty'); }`
- setOptionValue: callback to update the HTML of the option for a value (default: `function($option, value){ $option.css('background-color', value).addClass('empty'); }`

### Modifying the HTML of options

By using the `setIconValue` and `setOptionValue` options, it is possible to modify
the `<span>` elements that are used as the "buttons" for the picker.
For example, if you had a dropown that contained text options:

```HTML
<select name="choicespicker">
  <option value="A">Apple</option>
  <option value="B">Broccoli</option>
  <option value="C">Cheese</option>
</select>
```

To show images for each of the values, you could use these options:

```JavaScript
// using the same callback for both picker and options
var showImage = function($elem, value) {
  // create a new image and use the value as part of the source
  var $img = $('<img>').attr('src', '/img/food/' + value + '.jpg');
  $elem.empty().append($img));
};
$('select[name="choicespicker"]').simplepicker({
  picker: true,
  setOptionValue: showImage,
  setIconValue: showImage
});
```

## Browser support

SimplePicker supports all modern browsers starting with Internet Explorer 8 included.
It is recommended to not use any font theme with IE8.

## HTML5 new color input

HTML5 provides a new input to select colors. Its implementation inside modern browsers is still lacking.
The new color input does not provide any option to customize the color list and
most of the time the widget is less user-friendly than the one provided by simplepicker.

See http://slides.html5rocks.com/#new-form-types

See http://dev.w3.org/html5/markup/input.color.html#input.color

## Bower

```
bower install jquery-simplepicker
```

## Copyright and license

Licensed under the MIT license.
Copyright (C) 2012-2013 Tanguy Krotoff
Copyright (C) 2014 Ushahidi
