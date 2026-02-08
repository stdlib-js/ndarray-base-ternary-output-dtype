<!--

@license Apache-2.0

Copyright (c) 2026 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# ternaryOutputDataType

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Resolve the output ndarray [data type][@stdlib/ndarray/dtypes] for a ternary function.

<!-- Section to include introductory text. Make sure to keep an empty line after the intro `section` element and another before the `/section` close. -->

<section class="intro">

</section>

<!-- /.intro -->

<!-- Package usage documentation. -->



<section class="usage">

## Usage

To use in Observable,

```javascript
ternaryOutputDataType = require( 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-base-ternary-output-dtype@v0.1.1-umd/browser.js' )
```

To vendor stdlib functionality and avoid installing dependency trees for Node.js, you can use the UMD server build:

```javascript
var ternaryOutputDataType = require( 'path/to/vendor/umd/ndarray-base-ternary-output-dtype/index.js' )
```

To include the bundle in a webpage,

```html
<script type="text/javascript" src="https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-base-ternary-output-dtype@v0.1.1-umd/browser.js"></script>
```

If no recognized module system is present, access bundle contents via the global scope:

```html
<script type="text/javascript">
(function () {
    window.ternaryOutputDataType;
})();
</script>
```

#### ternaryOutputDataType( xdtype, ydtype, zdtype, policy )

Resolves the output ndarray [data type][@stdlib/ndarray/dtypes] for a ternary function according to a [data type policy][@stdlib/ndarray/output-dtype-policies].

```javascript
var dt = ternaryOutputDataType( 'int32', 'float32', 'float32', 'floating_point' );

var s = String( dt );
// returns 'float64'
```

The function supports the following parameters:

-   **xdtype**: first input ndarray [data type][@stdlib/ndarray/dtypes].
-   **ydtype**: second input ndarray [data type][@stdlib/ndarray/dtypes].
-   **zdtype**: third input ndarray [data type][@stdlib/ndarray/dtypes].
-   **policy**: output [data type policy][@stdlib/ndarray/output-dtype-policies].

If `policy` is a [data type][@stdlib/ndarray/dtypes], the function always returns the `policy` value (i.e., the third argument).

```javascript
var dt = ternaryOutputDataType( 'float32', 'float32', 'float32', 'float64' );

var s = String( dt );
// returns 'float64'

dt = ternaryOutputDataType( 'int32', 'int8', 'int32', 'float64' );

s = String( dt );
// returns 'float64'

// ...
```

</section>

<!-- /.usage -->

<!-- Package usage notes. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="notes">

## Notes

-   The function **always** applies [type promotion][@stdlib/ndarray/promotion-rules] to the provided data types, except for the following [data type policies][@stdlib/ndarray/output-dtype-policies]:

    -   `default`
    -   `default_index`
    -   `same`
    -   `<dtype>`

</section>

<!-- /.notes -->

<!-- Package usage examples. -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```html
<!DOCTYPE html>
<html lang="en">
<body>
<script type="text/javascript" src="https://cdn.jsdelivr.net/gh/stdlib-js/utils-nary-function@umd/browser.js"></script>
<script type="text/javascript" src="https://cdn.jsdelivr.net/gh/stdlib-js/utils-unzip@umd/browser.js"></script>
<script type="text/javascript" src="https://cdn.jsdelivr.net/gh/stdlib-js/array-base-n-cartesian-product@umd/browser.js"></script>
<script type="text/javascript" src="https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-dtypes@umd/browser.js"></script>
<script type="text/javascript" src="https://cdn.jsdelivr.net/gh/stdlib-js/console-log-each-map@umd/browser.js"></script>
<script type="text/javascript" src="https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-base-ternary-output-dtype@v0.1.1-umd/browser.js"></script>
<script type="text/javascript">
(function () {

// Get the list of real-valued floating-point data types:
var dt = dtypes( 'real_floating_point' );

// Define a list of output data type policies:
var policies = [
    'default',
    'real',
    'floating_point',
    'complex_floating_point'
];

// Generate dtype-policy Cartesian products:
var args = nCartesianProduct( dt, dt, dt, policies );

// Unzip the argument pair array:
args = unzip( args );

// Resolve output data types:
logEachMap( 'dtypes: (%7s, %7s, %7s). policy: %-24s. output dtype: %s.', args[ 0 ], args[ 1 ], args[ 2 ], args[ 3 ], naryFunction( ternaryOutputDataType, 4 ) );

})();
</script>
</body>
</html>
```

</section>

<!-- /.examples -->

<!-- Section to include cited references. If references are included, add a horizontal rule *before* the section. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="references">

</section>

<!-- /.references -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library for JavaScript and Node.js, with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2026. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/ndarray-base-ternary-output-dtype.svg
[npm-url]: https://npmjs.org/package/@stdlib/ndarray-base-ternary-output-dtype

[test-image]: https://github.com/stdlib-js/ndarray-base-ternary-output-dtype/actions/workflows/test.yml/badge.svg?branch=v0.1.1
[test-url]: https://github.com/stdlib-js/ndarray-base-ternary-output-dtype/actions/workflows/test.yml?query=branch:v0.1.1

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/ndarray-base-ternary-output-dtype/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/ndarray-base-ternary-output-dtype?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/ndarray-base-ternary-output-dtype.svg
[dependencies-url]: https://david-dm.org/stdlib-js/ndarray-base-ternary-output-dtype/main

-->

[chat-image]: https://img.shields.io/badge/zulip-join_chat-brightgreen.svg
[chat-url]: https://stdlib.zulipchat.com

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/ndarray-base-ternary-output-dtype/tree/deno
[deno-readme]: https://github.com/stdlib-js/ndarray-base-ternary-output-dtype/blob/deno/README.md
[umd-url]: https://github.com/stdlib-js/ndarray-base-ternary-output-dtype/tree/umd
[umd-readme]: https://github.com/stdlib-js/ndarray-base-ternary-output-dtype/blob/umd/README.md
[esm-url]: https://github.com/stdlib-js/ndarray-base-ternary-output-dtype/tree/esm
[esm-readme]: https://github.com/stdlib-js/ndarray-base-ternary-output-dtype/blob/esm/README.md
[branches-url]: https://github.com/stdlib-js/ndarray-base-ternary-output-dtype/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/ndarray-base-ternary-output-dtype/main/LICENSE

[@stdlib/ndarray/dtypes]: https://github.com/stdlib-js/ndarray-dtypes/tree/umd

[@stdlib/ndarray/output-dtype-policies]: https://github.com/stdlib-js/ndarray-output-dtype-policies/tree/umd

[@stdlib/ndarray/promotion-rules]: https://github.com/stdlib-js/ndarray-promotion-rules/tree/umd

</section>

<!-- /.links -->
