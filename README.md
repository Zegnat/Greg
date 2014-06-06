# Zegnat/Greg

Based on [Greg by Everywhere.is](https://github.com/everywhereis/Greg), where it is described as:

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

## Greg vs. Zegnat/Greg

Greg was [presented](http://everywhere.is/opinionated/greg-a-super-simple-sass-mixin/) with a basic grid example based on the following HTML:

```html
<ul class="gregWrapper">
    <li class="col col_1"></li>
    <li class="col col_1"></li>
    <li class="col col_1"></li>
    <li class="col col_1"></li>
    <li class="col col_1"></li>
    <li class="col col_1"></li>
    <li class="col col_1"></li>
    <li class="col col_1"></li>
    <li class="col col_1"></li>
    <li class="col col_1"></li>
</ul>
<ul class="gregWrapper">
    <li class="col col_10"></li>
</ul>
<ul class="gregWrapper">
    <li class="col col_7"></li>
    <li class="col col_3"></li>
</ul>
<ul class="gregWrapper">
    <li class="col col_10"></li>
</ul>
<ul class="gregWrapper">
    <li class="col col_2"></li>
    <li class="col col_2"></li>
    <li class="col col_2"></li>
    <li class="col col_2"></li>
    <li class="col col_2"></li>
</ul>
```

And the mixin was called as follows:

```scss
.gregWrapper { @include greg(10, 2%); }
```

In the original Greg this resulted in:

```css
.gregWrapper .col_10 {
  width: 100%;
  float: left;
  display: block;
  margin-left: 2%; }
.gregWrapper .col_10:first-child {
  margin-left: 0; }
@media only screen and (max-width: 480px) {
  .gregWrapper .col_10 {
    width: 100%;
    margin-left: 0; } }
.gregWrapper .col_9 {
  width: 89.8%;
  float: left;
  display: block;
  margin-left: 2%; }
.gregWrapper .col_9:first-child {
  margin-left: 0; }
@media only screen and (max-width: 480px) {
  .gregWrapper .col_9 {
    width: 100%;
    margin-left: 0; } }
.gregWrapper .col_8 {
  width: 79.6%;
  float: left;
  display: block;
  margin-left: 2%; }
.gregWrapper .col_8:first-child {
  margin-left: 0; }
@media only screen and (max-width: 480px) {
  .gregWrapper .col_8 {
    width: 100%;
    margin-left: 0; } }
.gregWrapper .col_7 {
  width: 69.4%;
  float: left;
  display: block;
  margin-left: 2%; }
.gregWrapper .col_7:first-child {
  margin-left: 0; }
@media only screen and (max-width: 480px) {
  .gregWrapper .col_7 {
    width: 100%;
    margin-left: 0; } }
.gregWrapper .col_6 {
  width: 59.2%;
  float: left;
  display: block;
  margin-left: 2%; }
.gregWrapper .col_6:first-child {
  margin-left: 0; }
@media only screen and (max-width: 480px) {
  .gregWrapper .col_6 {
    width: 100%;
    margin-left: 0; } }
.gregWrapper .col_5 {
  width: 49.0%;
  float: left;
  display: block;
  margin-left: 2%; }
.gregWrapper .col_5:first-child {
  margin-left: 0; }
@media only screen and (max-width: 480px) {
  .gregWrapper .col_5 {
    width: 100%;
    margin-left: 0; } }
.gregWrapper .col_4 {
  width: 38.8%;
  float: left;
  display: block;
  margin-left: 2%; }
.gregWrapper .col_4:first-child {
  margin-left: 0; }
@media only screen and (max-width: 480px) {
  .gregWrapper .col_4 {
    width: 100%;
    margin-left: 0; } }
.gregWrapper .col_3 {
  width: 28.6%;
  float: left;
  display: block;
  margin-left: 2%; }
.gregWrapper .col_3:first-child {
  margin-left: 0; }
@media only screen and (max-width: 480px) {
  .gregWrapper .col_3 {
    width: 100%;
    margin-left: 0; } }
.gregWrapper .col_2 {
  width: 18.4%;
  float: left;
  display: block;
  margin-left: 2%; }
.gregWrapper .col_2:first-child {
  margin-left: 0; }
@media only screen and (max-width: 480px) {
  .gregWrapper .col_2 {
    width: 100%;
    margin-left: 0; } }
.gregWrapper .col_1 {
  width: 8.2%;
  float: left;
  display: block;
  margin-left: 2%; }
.gregWrapper .col_1:first-child {
  margin-left: 0; }
@media only screen and (max-width: 480px) {
  .gregWrapper .col_1 {
    width: 100%;
    margin-left: 0; } }
```

Using Zegnat/Greg and its limiter function the SASS would be:

```scss
.gregWrapper { @include greg(10, 2%, 480px, 1 10 7 3 2); }
```

And the output only:

```css
.gregWrapper .col_1 {
  width: 8.2%; }
.gregWrapper .col_2 {
  width: 18.4%; }
.gregWrapper .col_3 {
  width: 28.6%; }
.gregWrapper .col_7 {
  width: 69.4%; }
.gregWrapper .col_10 {
  width: 100%; }
.gregWrapper .col_1, .gregWrapper .col_2, .gregWrapper .col_3, .gregWrapper .col_7, .gregWrapper .col_10 {
  display: block;
  float: left;
  margin-left: 2%; }
  .gregWrapper .col_1:first-child, .gregWrapper .col_2:first-child, .gregWrapper .col_3:first-child, .gregWrapper .col_7:first-child, .gregWrapper .col_10:first-child {
    margin-left: 0; }
  @media only screen and (max-width: 480px) {
    .gregWrapper .col_1, .gregWrapper .col_2, .gregWrapper .col_3, .gregWrapper .col_7, .gregWrapper .col_10 {
      margin-left: 0;
      width: 100%; } }
```

## Licence

Greg is released under [the MIT license](LICENSE). The original version and API by Everywhere.is and this rewritten version with its space-saving features by Martijn van der Ven.
