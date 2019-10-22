# jQuery Custom Select Plugin

The drop-down list for the select field itself is almost not styled. This plugin adds blocks around it and creates the necessary event handlers. So you can stylize the look of these blocks using the CSS. The plugin simplifies website development.

The CSS file contains only the properties required for the functioning of the drop-down list and the field with the selection result. You need to stylize them yourself.

Based on [Custom Select Menu](https://codepen.io/wallaceerick/pen/ctsCz), CodePen by [Wallace Erick](https://codepen.io/wallaceerick).


## The plugin creates 3 blocks and uses 4 style classes

```html
<div class="custom-select">
	<select class="your-select-field custom-select__hidden">
		<option value="apple" selected>Apple</option>
		<option value="banana">Banana</option>
		<option value="carrot">Carrot</option>
	</select>
	<div class="custom-select__styled" tabindex="0">Apple</div>
	<ul class="custom-select__list" style="display: none;">
		<li rel="apple"  tabindex="0" class="custom-select__elected">Apple</li>
		<li rel="banana" tabindex="0">Banana</li>
		<li rel="carrot" tabindex="0">Carrot</li>
	</ul>
</div>
```


| Option        | Default value              | Role                                                                                       |
| :---          | :---                       | :---                                                                                       |
| classSelect   | `.custom-select`           | CSS class for a `<div>` that wraps the original <select> and the blocks we're going to add |
| classHidden   | classSelect + `__hidden`   | CSS class for the original `<select>` to make it hidden                                    |
| classList     | classSelect + `__list`     | CSS class for a `<ul>` that shows the list of the options for selection                    |
| classSelected | classSelect + `__selected` | CSS class for the selected item in the drop-down list                                      |
| classStyled   | classSelect + `__styled`   | CSS class for a `<div>` that shows the selected option                                     |


If the original `<select>` has no selected option yet, the plugin defines the first option as a selected one.


## HTML attributes

The plugin copies the `class` and `style` attributes from each `<option>` tag to the corresponding `<li>` tag as is.

If `<option>` tag has the `data-html` attribute. then the plugin places this HTML as a content of the depending `<li>` tag.

So you can use images in the layout of options and customize the appearance of these images using CSS properties.

For example, the plugin will turn such HTML source code:

```html
<select class="your-select-field">
	<option value="apple" class="apple-class" style="background-image:url('/images/apple.jpg');">Apple</option>
	<option value="banana" data-html="<img class='custom-select__image' src='/images/banana.jpg' />Banana">Banana</option>
</select>
```

into such final code:

```html
<div class="custom-select">
	<select class="your-select-field custom-select__hidden">
...
	</select>
	<div class="custom-select__styled" tabindex="0">Apple</div>
	<ul class="custom-select__list">
		<li rel="apple" class="apple-class" style="background-image:url('/images/apple.jpg');">Apple</li>
		<li rel="banana">
			<img class="custom-select__image" src="/images/banana.jpg" />
			Banana
		</li>
	</ul>
</div>
```


## Event handlers

Trigger `change` event on the select field after updating the value. So your `onchange` handlers would work too.

Keyboard:
Open drop-down list by `Space` or `Enter`.
Close drop-down list by second by `Space` or `Enter`, by `Esc` (and by click outside).
Go to next option by `Tab`.
Choose item by `Space` or `Enter`


## How to use

1) Include jquery-custom-select.js in your page.
1) Include jquery-custom-select.css or use it as a basis for your styles.
2) Create your own style classes.
3) Call the `.customSelect()` method, passing it the names of the style classes as parameters:

```js
$('.your-select-field').customSelect();

$('.your-select-field').customSelect('.your-main-customization-class');

$('.your-select-field').customSelect(array(
	classSelect: '.your-main-customization-class',
	classHidden: '.your-class-to-hide-the-original-select',
	classList:   '.your-class-for-the-dropdown-list',
	classStyled: '.your-class-for-the-div-with-the-result-of-select',
));
```
