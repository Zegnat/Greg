# Zegnat/Greg

Based on [Greg by Everywhere.is](https://github.com/everywhereis/Greg), where it is subscribed as:

> […] an Über simple responsive and fluid grid mixin for Sass.

The name is an abbreviation for “great responsive easy grids”. The mixin is completely compatible with the superior SASS compiler [Libsass](http://libsass.org).

## Usage

### Basic usage

Greg builds a basic column grid based on a defined number of columns and gutter width. This example will generate a 5 column grid with 2% wide gutters:

```scss
@include greg(5, 2%);
```

Using classes ranged from `col_1` through `col_5` will allow for columns of different widths to be used in the design. For example:

```html
<div class="container">
    <div class="col_2"></div>
    <div class="col_3"></div>
</div>
```

Will result in one column spanning the first 2 grid columns followed by one filling the last 3, for a total of 5 columns. Note that there is no container class included in Greg.

### Setting a mobile breakpoint

Greg takes a single breakpoint where the columns will collapse and be displayed below eachother. By default this happens on screens with a width of 480 pixels or less. But this width can be set to anything using a third parameter:

```scss
@include greg(5, 2%, 240px);
```

### Limiting the output classes

Zegnat/Greg was made to have a smaller generated (output) CSS than its previous version. As such a fourth parameter can be passed to specify the column widths you are planning to use.

In the basic usage example Greg will generate classes for all 5 possible column widths even though our HTML only uses 2 (`col_2` and `col_3`). The fourth parameter can be set so Greg will only generate the specific classes `col_2` and `col_3`:

```scss
@include greg(5, 2%, 480px, 2 3)
```

Any valid [SASS list](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#lists) of numbers will work, as long as the numbers are within the number of columns specified in the first parameter.

## Licence

Greg is released under [the MIT license](LICENSE). The original version and API by Everywhere.is and this rewritten version with its space-saving features by Martijn van der Ven.