<h1>🚀 Getting Started</h1>

<img align="right" height="130" alt="Throw package" src="https://img.icons8.com/color/1080/recurring-appointment-exception--v1.png">

<p>In this package provides Sass variables, mixins and functions to standardize exception messages.</p>
<p>To use this package, use the @use rule in each of your files as below:</p>

```scss
@use "alapnian-sass/throw";
```

<details>
    <summary>See the list of available mixins</summary>
    <dl>
        <dt><a href="#variable"><code>variable($message, $names, $catch: false)</code></a></dt>
        <dd>Output an error message stating an issue with one or more variables.</dd>
        <dt><a href="variable-type"><code>variable-type($name, $value, $types, $message: null, $catch: false)</code></a></dt>
        <dd>Output an error message stating a variable received the wrong type.</dd>
        <dt><a href="#parameter"><code>parameter($message, $context, $names, $catch: false)</code></a></dt>
        <dd>Output an error message stating an issue with one or more parameters.</dd>
        <dt><a href="#parameter-type"><code>parameter-type($context, $name, $value, $types, $message: null, $catch: false)</code></a></dt>
        <dd>Output an error message stating a parameter received the wrong type.</dd>
        <dt><a href="#separator"><code>separator($context: null, $catch: false)</code></a></dt>
        <dd>Output an error message stating a separator of variable or mixin parameter received the wrong value.</dd>
    </dl>
</details>

<details>
    <summary>See the list of available functions</summary>
    <dl>
        <dt><a href="#parameter-1"><code>parameter($message, $context, $names, $catch: false)</code></a></dt>
        <dd>Return an error message stating an issue with one or more parameters.</dd>
        <dt><a href="#parameter-type-1"><code>parameter-type($context, $name, $value, $types, $message: null, $catch: false)</code></a></dt>
        <dd>Return an error message stating a parameter received the wrong type.</dd>
        <dt><a href="#separator-1"><code>separator($name, $context: null, $catch: false)</code></a></dt>
        <dd>Return an error message stating a separator of variable or mixin parameter received the wrong value.</dd>
    </dl>
</details>

<h1>🌀 Mixins</h1>

<h2>variable</h2>

```scss
throw.variable($message, $names, $catch: false);

variable-exception($message, $names, $catch: false);
```
<p>Output an error message stating an issue with one or more variables.</p>

<p><strong><i>Parameters:</i></strong></p>
<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Default</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>$message</code></td>
            <td><a href="https://sass-lang.com/documentation/values/strings/">String</a></td>
            <td></td>
            <td>The message which describes the issue.</td>
        </tr>
        <tr>
            <td><code>$names</code></td>
            <td><a href="https://sass-lang.com/documentation/values/lists/#argument-lists">ArgList</a></td>
            <td></td>
            <td>The names of the variables for which there is an issue.</td>
        </tr>
        <tr>
            <td><code>$catch</code></td>
            <td><a href="https://sass-lang.com/documentation/values/booleans/">Bool</a> | <code>'warn'</code></td>
            <td><code>false</code></td>
            <td>Optionally catch errors, and output them as CSS comments without stopping compilation.</td>
        </tr>
    </tbody>
</table>

<p><strong><i>Output:</i></strong></p>
<p>A string describing the reason one or more variables are misconfigured.</p>

<p><strong><i>Example:</i></strong></p>
<details>
    <summary>Using Namespace</summary>
    
```scss
@use "alapnian-sass/throw";

$width: 1080;

@if $width <= 1080 {
    @include throw.variable(
        "",
        "width",
        $catch: false
    );
}
```
</details>
<details>
    <summary>Without Namespace</summary>
    
```scss
$width: 1080;

@if $width <= 1080 {
    @include variable-exception(
        "",
        "width",
        $catch: false
    );
}
```
</details>

<h2>variable-type</h2>

```scss
throw.variable-type($name, $value, $types, $message: null, $catch: false);

variable-type-exception($name, $value, $types, $message: null, $catch: false);
```
<p>Output an error message stating a variable received the wrong type.</p>

<p><strong><i>Parameters:</i></strong></p>
<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Default</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>$name</code></td>
            <td><a href="https://sass-lang.com/documentation/values/strings/">String</a></td>
            <td></td>
            <td>The name of the variable which has received the wrong type.</td>
        </tr>
        <tr>
            <td><code>$value</code></td>
            <td>*</td>
            <td></td>
            <td>The value which was received.</td>
        </tr>
        <tr>
            <td><code>$types</code></td>
            <td><a href="https://sass-lang.com/documentation/values/lists/#argument-lists">ArgList</a></td>
            <td></td>
            <td>The types which are expected.</td>
        </tr>
        <tr>
            <td><code>$message</code></td>
            <td><a href="https://sass-lang.com/documentation/values/strings/">String</a> | <a href="https://sass-lang.com/documentation/values/null/"><code>null</code></a></td>
            <td><code>null</code></td>
            <td>The additional message which describes the issue. Must be passed by name.</td>
        </tr>
        <tr>
            <td><code>$catch</code></td>
            <td><a href="https://sass-lang.com/documentation/values/booleans/">Bool</a> | <code>'warn'</code></td>
            <td><code>false</code></td>
            <td>Optionally catch errors, and output them as CSS comments without stopping compilation.</td>
        </tr>
    </tbody>
</table>

<p><strong><i>Output:</i></strong></p>
<p>A string describing what types are acceptable for a variable and the value that is misconfigured.</p>

<p><strong><i>Example:</i></strong></p>
<details>
    <summary>Using Namespace</summary>
    
```scss
@use "sass:meta";
@use "alapnian-sass/throw";

$width: 1080;

@if meta.type-of($width) != 'number' {
    @include throw.variable-type(
        "width",
        $width,
        "number",
        $message: "",
        $catch: false
    );
}
```
</details>
<details>
    <summary>Without Namespace</summary>
    
```scss
$width: 1080;

@if type-of($width) != 'number' {
    @include variable-type-exception(
        "width",
        $width,
        "number",
        $message: "",
        $catch: false
    );
}
```
</details>

<h2>parameter</h2>

```scss
throw.parameter($message, $context, $names, $catch: false);

parameter-exception($message, $context, $names, $catch: false);
```
<p>Output an error message stating an issue with one or more parameters.</p>

<p><strong><i>Parameters:</i></strong></p>
<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Default</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>$message</code></td>
            <td><a href="https://sass-lang.com/documentation/values/strings/">String</a></td>
            <td></td>
            <td>The message which describes the issue.</td>
        </tr>
        <tr>
            <td><code>$context</code></td>
            <td><a href="https://sass-lang.com/documentation/values/strings/">String</a></td>
            <td></td>
            <td>The name of the mixin issuing the error.</td>
        </tr>
        <tr>
            <td><code>$names</code></td>
            <td><a href="https://sass-lang.com/documentation/values/lists/#argument-lists">ArgList</a></td>
            <td></td>
            <td>The names of the parameters for which there is an issue.</td>
        </tr>
        <tr>
            <td><code>$catch</code></td>
            <td><a href="https://sass-lang.com/documentation/values/booleans/">Bool</a> | <code>'warn'</code></td>
            <td><code>false</code></td>
            <td>Optionally catch errors, and output them as CSS comments without stopping compilation.</td>
        </tr>
    </tbody>
</table>

<p><strong><i>Output:</i></strong></p>
<p>A string describing the reason one or more parameters are invalid.</p>

<p><strong><i>Example:</i></strong></p>
<details>
    <summary>Using Namespace</summary>
    
```scss
@use "sass:list";
@use "sass:string";
@use "alapnian-sass/throw";

@mixin resizable($direction) {
    @if index(none both horizontal vertical block inline, $direction) != null {
        resize: string.unquote($direction);
    } @else {
        @include throw.parameter(
            'Must be "none", or "both", or "horizontal", or "vertical", or "block".'
            'resizable',
            'direction',
            $catch: false 
        );
    }

}

.invalid-resizable {
    @include resizable('diagonal');
}

.valid-resizable {
    @include resizable('vertical');
}
```
</details>
<details>
    <summary>Without Namespace</summary>
    
```scss
@mixin resizable($direction) {
    @if index(none both horizontal vertical block inline, $direction) != null {
        resize: unquote($direction);
    } @else {
        @include parameter-exception(
            'Must be "none", or "both", or "horizontal", or "vertical", or "block".'
            'resizable',
            'direction',
            $catch: false 
        );
    }
}

.invalid-resizable {
    @include resizable('diagonal');
}

.valid-resizable {
    @include resizable('vertical');
}
```
</details>

<h2>parameter-type</h2>

```scss
throw.parameter-type($context, $name, $value, $types, $message: null, $catch: false);

parameter-type-exception($context, $name, $value, $types, $message: null, $catch: false);
```
<p>Output an error message stating a parameter received the wrong type.</p>

<p><strong><i>Parameters:</i></strong></p>
<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Default</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>$context</code></td>
            <td><a href="https://sass-lang.com/documentation/values/strings/">String</a></td>
            <td></td>
            <td>The name of the mixin issuing the error.</td>
        </tr>
        <tr>
            <td><code>$name</code></td>
            <td><a href="https://sass-lang.com/documentation/values/strings/">String</a></td>
            <td></td>
            <td>The name of the parameter which has received the wrong type.</td>
        </tr>
        <tr>
            <td><code>$value</code></td>
            <td>*</td>
            <td></td>
            <td>The value which was received.</td>
        </tr>
        <tr>
            <td><code>$types</code></td>
            <td><a href="https://sass-lang.com/documentation/values/lists/#argument-lists">ArgList</a></td>
            <td></td>
            <td>The types which are expected.</td>
        </tr>
        <tr>
            <td><code>$message</code></td>
            <td><a href="https://sass-lang.com/documentation/values/strings/">String</a> | <a href="https://sass-lang.com/documentation/values/null/"><code>null</code></a></td>
            <td><code>null</code></td>
            <td>The additional message which describes the issue. Must be passed by name.</td>
        </tr>
        <tr>
            <td><code>$catch</code></td>
            <td><a href="https://sass-lang.com/documentation/values/booleans/">Bool</a> | <code>'warn'</code></td>
            <td><code>false</code></td>
            <td>Optionally catch errors, and output them as CSS comments without stopping compilation.</td>
        </tr>
    </tbody>
</table>

<p><strong><i>Output:</i></strong></p>
<p>A string describing what types are acceptable for a parameter and the value that is invalid.</p>

<p><strong><i>Example:</i></strong></p>
<details>
    <summary>Using Namespace</summary>
    
```scss
@use "sass:meta";
@use "alapnian-sass/throw";

@mixin background-color($color) {
    @if meta.type-of($color) == 'string' {
        background-color: #{$color};
    } @else {
        @include throw.parameter-type(
            'background-color'
            'color',
            $color,
            'color',
            $message: 'Color values can be color names, or hex colors, or rgb(), or hsl(), or hwb(), or lab(), or lch(), or oklab(), or oklch(), or color().',
            $catch: false 
        );
    }

}

.bg-invalid {
    @include background-color(123);
}

.bg-hex {
    @include background-color(#fff);
}
.bg-rgb {
    @include background-color(rgb(255,255,255));
}
```
</details>
<details>
    <summary>Without Namespace</summary>
    
```scss
@mixin background-color($color) {
    @if type-of($color) == 'string' {
        background-color: #{$color};
    } @else {
        @include parameter-type-exception(
            'background-color'
            'color',
            $color,
            'color',
            $message: 'Color values can be color names, or hex colors, or rgb(), or hsl(), or hwb(), or lab(), or lch(), or oklab(), or oklch(), or color().',
            $catch: false 
        );
    }

}

.bg-invalid {
    @include background-color(123);
}

.bg-hex {
    @include background-color(#fff);
}
.bg-rgb {
    @include background-color(rgb(255,255,255));
}
```
</details>

<h2>separator</h2>

```scss
throw.separator($context: null, $catch: false);

parameter-type-exception($context: null, $catch: false);
```
<p>Output an error message stating a separator of variable or mixin parameter received the wrong value.</p>

<p><strong><i>Parameters:</i></strong></p>
<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Default</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>$context</code></td>
            <td><a href="https://sass-lang.com/documentation/values/strings/">String</a> | <a href="https://sass-lang.com/documentation/values/null/"><code>null</code></a></td>
            <td><code>null</code></td>
            <td>The name of the mixin issuing the error.</td>
        </tr>
        <tr>
            <td><code>$catch</code></td>
            <td><a href="https://sass-lang.com/documentation/values/booleans/">Bool</a> | <code>'warn'</code></td>
            <td><code>false</code></td>
            <td>Optionally catch errors, and output them as CSS comments without stopping compilation.</td>
        </tr>
    </tbody>
</table>

<p><strong><i>Output:</i></strong></p>
<p>A string describing what values are acceptable for a separator.</p>

<p><strong><i>Example:</i></strong></p>
<details>
    <summary>Using Namespace</summary>
    <p>Validating the separator settings set on the variable:</p>

```scss
@use "sass:list";
@use "alapnian-sass/throw";

$valid-separator: auto;

@if list.index(space comma slash auto, $valid-separator) {
    @include throw.separator(
        $name: 'valid-separator',
        $catch: false
    );
}

$invalid-separator: dot;

@if list.index(space comma slash auto, $invalid-separator) {
    @include throw.separator(
        $name: 'invalid-separator',
        $catch: false
    );
}
```
</details>
<details>
    <summary>Without Namespace</summary>
    
```scss
$valid-separator: auto;

@if index(space comma slash auto, $valid-separator) {
    @include throw.separator(
        $name: 'valid-separator',
        $catch: false
    );
}

$invalid-separator: dot;

@if list.index(space comma slash auto, $invalid-separator) {
    @include throw.separator(
        $name: 'invalid-separator',
        $catch: false
    );
}
```
</details>

<h1>🛠️ Function</h1>

<h2>parameter</h2>

```scss
throw.parameter($message, $context, $names, $catch: false); //=> string

parameter-exception($message, $context, $names, $catch: false); //=> string
```
<p>Return an error message stating an issue with one or more parameters.</p>

<p><strong><i>Parameters:</i></strong></p>
<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Default</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>$message</code></td>
            <td><a href="https://sass-lang.com/documentation/values/strings/">String</a></td>
            <td></td>
            <td>The message which describes the issue.</td>
        </tr>
        <tr>
            <td><code>$context</code></td>
            <td><a href="https://sass-lang.com/documentation/values/strings/">String</a></td>
            <td></td>
            <td>The name of the mixin issuing the error.</td>
        </tr>
        <tr>
            <td><code>$names</code></td>
            <td><a href="https://sass-lang.com/documentation/values/lists/#argument-lists">ArgList</a></td>
            <td></td>
            <td>The names of the parameters for which there is an issue.</td>
        </tr>
        <tr>
            <td><code>$catch</code></td>
            <td><a href="https://sass-lang.com/documentation/values/booleans/">Bool</a> | <code>'warn'</code></td>
            <td><code>false</code></td>
            <td>Optionally catch errors, and output them as CSS comments without stopping compilation.</td>
        </tr>
    </tbody>
</table>

<p><strong><i>Return Value:</i></strong></p>
<dl>
    <dt><a href="https://sass-lang.com/documentation/values/strings/">String</a></dt>
    <dd>A string describing the reason one or more parameters are invalid.</dd>
</dl>

<p><strong><i>Example:</i></strong></p>
<details>
    <summary>Using Namespace</summary>
    
```scss
@use "sass:list";
@use "sass:map";
@use "alapnian-sass/throw";

@function from($pairs...) {
    @if list.length($pairs) < 1 {
        @return throw.parameter(
            'One or more key/value pairs are required',
            'from',
            'pairs',
            $catch: false
        );
    }

    $result: ();

    @each $key, $value in $pairs {
        $result: map.merge($result, $key, $value);
    }

    @return $result;
}

// Invalid
@debug from();
// Valid
@debug from($number: 10);
```
</details>
<details>
    <summary>Without Namespace</summary>
    
```scss
@function from($pairs...) {
    @if length($pairs) < 1 {
        @return parameter-exception(
            'One or more key/value pairs are required',
            'from',
            'pairs',
            $catch: false
        );
    }

    $result: ();

    @each $key, $value in $pairs {
        $result: map-merge($result, $key, $value);
    }

    @return $result;
}

// Invalid
@debug from();
// Valid
@debug from($number: 10);
```
</details>

<h2>parameter-type</h2>

```scss
throw.parameter-type($context, $name, $value, $types, $message: null, $catch: false); //=> string

parameter-type-exception($context, $name, $value, $types, $message: null, $catch: false); //=> string
```
<p>Return an error message stating a parameter received the wrong type.</p>

<p><strong><i>Parameters:</i></strong></p>
<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Default</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>$context</code></td>
            <td><a href="https://sass-lang.com/documentation/values/strings/">String</a></td>
            <td></td>
            <td>The name of the mixin issuing the error.</td>
        </tr>
        <tr>
            <td><code>$name</code></td>
            <td><a href="https://sass-lang.com/documentation/values/strings/">String</a></td>
            <td></td>
            <td>The name of the parameter which has received the wrong type.</td>
        </tr>
        <tr>
            <td><code>$value</code></td>
            <td>*</td>
            <td></td>
            <td>The value which was received.</td>
        </tr>
        <tr>
            <td><code>$types</code></td>
            <td><a href="https://sass-lang.com/documentation/values/lists/#argument-lists">ArgList</a></td>
            <td></td>
            <td>The types which are expected.</td>
        </tr>
        <tr>
            <td><code>$message</code></td>
            <td><a href="https://sass-lang.com/documentation/values/strings/">String</a> | <a href="https://sass-lang.com/documentation/values/null/"><code>null</code></a></td>
            <td><code>null</code></td>
            <td>The additional message which describes the issue. Must be passed by name.</td>
        </tr>
        <tr>
            <td><code>$catch</code></td>
            <td><a href="https://sass-lang.com/documentation/values/booleans/">Bool</a> | <code>'warn'</code></td>
            <td><code>false</code></td>
            <td>Optionally catch errors, and output them as CSS comments without stopping compilation.</td>
        </tr>
    </tbody>
</table>

<p><strong><i>Return Value:</i></strong></p>
<dl>
    <dt><a href="https://sass-lang.com/documentation/values/strings/">String</a></dt>
    <dd>A string describing what types are acceptable for a parameter and the value that is invalid.</dd>
</dl>

<p><strong><i>Example:</i></strong></p>
<details>
    <summary>Using Namespace</summary>
    
```scss
@use "sass:meta";
@use "alapnian-sass/throw";

@function tint-color($color, $weight) {
    @if meta.type-of($color) != 'color' {
        @return throw.parameter-type(
            'tint-color',
            'color',
            $color,
            'color',
            $message: null,
            $catch: false
        );
    }
}

// Invalid
@debug tint-color(true, 90%);
// Valid
@debug tint-color(gray, 90%);
```
</details>
<details>
    <summary>Without Namespace</summary>
    
```scss
@function tint-color($color, $weight) {
    @if type-of($color) != 'color' {
        @return parameter-type-exception(
            'tint-color',
            'color',
            $color,
            'color',
            $message: null,
            $catch: false
        );
    }
}

// Invalid
@debug tint-color(true, 90%);
// Valid
@debug tint-color(gray, 90%);
```
</details>

<h2>separator</h2>

```scss
throw.separator($name, $context: null, $catch: false);

separator-exception($name, $context: null, $catch: false);
```
<p>Return an error message stating a separator of function parameter received the wrong value.</p>

<p><strong><i>Parameters:</i></strong></p>
<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Default</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>$name</code></td>
            <td><a href="https://sass-lang.com/documentation/values/strings/">String</a></td>
            <td>'separator'</td>
            <td>The name of the variables/parameters for which there is an issue.</td>
        </tr>
        <tr>
            <td><code>$context</code></td>
            <td><a href="https://sass-lang.com/documentation/values/strings/">String</a> | <a href="https://sass-lang.com/documentation/values/null/"><code>null</code></a></td>
            <td><code>null</code></td>
            <td>The name of the function issuing the error.</td>
        </tr>
        <tr>
            <td><code>$catch</code></td>
            <td><a href="https://sass-lang.com/documentation/values/booleans/">Bool</a> | <code>'warn'</code></td>
            <td><code>false</code></td>
            <td>Optionally catch errors, and output them as CSS comments without stopping compilation.</td>
        </tr>
    </tbody>
</table>

<p><strong><i>Return Value:</i></strong></p>
<dl>
    <dt><a href="https://sass-lang.com/documentation/values/strings/">String</a></dt>
    <dd>A string describing what values are acceptable for a separator.</dd>
</dl>

<p><strong><i>Example:</i></strong></p>
<details>
    <summary>Using Namespace</summary>
    <p>Validating the separator settings set on the variable:</p>

```scss
@use "sass:list";
@use "alapnian-sass/throw";

@function add($list, $value, $separator: auto) {
    @if list.index(comma space slash auto, $separator) == null {
        @return throw.separator('add', 'separator', $catch: false);
    }

    @return list.append($list, $value, $separator);
}
```
</details>
<details>
    <summary>Without Namespace</summary>
    
```scss
@function add($list, $value, $separator: auto) {
    @if index(comma space slash auto, $separator) == null {
        @return separator-exception('add', 'separator', $catch: false);
    }

    @return append($list, $value, $separator);
}
```
</details>