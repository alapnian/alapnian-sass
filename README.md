<p align="center">
    <a target="_blank" href="https://alapnian.com/"><img height="100" src="https://github.com/alapnian.png"/></a>&nbsp;
    <a target="_blank" href="https://sass-lang.com/"><img height="100" src="https://sass-lang.com/assets/img/logos/logo.svg"/></a>
</p>

<h1 align="center">
    Alapnian Sass
</h1>

<p align="center">Provides extended variables, mixins and functions for Sass.</p>

<p align="center">
    <a target="_blank" href="https://www.npmjs.com/package/alapnian-sass"><img alt="Version" src="https://img.shields.io/npm/v/alapnian-sass"/></a>&nbsp;
    <a target="_blank" href="https://npmtrends.com/alapnian-sass"><img alt="Download" src="https://img.shields.io/npm/dy/alapnian-sass"/></a>&nbsp;
    <a target="_blank" href="LICENSE"><img alt="License" src="https://img.shields.io/github/license/alapnian/alapnian-sass"/></a>
</p>

<p align="center">
    <a href="https://github.com/alapnian/alapnian-sass">Home</a>&nbsp;•&nbsp;
    <a href="#package">Package</a>&nbsp;•&nbsp;
    <a href="#getting-started">Getting Started</a>&nbsp;•&nbsp;
    <a target="_blank" href="">Wiki</a>&nbsp;•&nbsp;
    <a href="#license">License</a>
</p>

<h2>Package</h2>
<dl>
    <dt><a target="_blank" href="https://github.com/alapnian/sass-modules/wiki/Package#-throw"><code>alapnian-sass/throw</code></a> <sup><span style="color: gold;">New</span></sup></dt>
    <dd>Provides Sass functions to standardize exception messages.</dd>
</dl>

<h2>Getting Started</h2>

<h3>Require</h3>

<ul>
    <li>Sass 1.89.2 compiled with dart2js 3.8.1</li>
</ul>

<h3>Installation</h3>
<h4>Node Package Manager</h4>

```bash
npm i alapnian-sass
```

<h4>Manual</h4>
<p>Download <a href="https://github.com/alapnian/alapnian-sass/releases">the latest release</a></p>

<h3>How To Use</h3>

<h4>Using <code>@use</code> rule</h4>

```scss
@use "alapnian-sass/throw";

$width: 1080;

@if $width < 1080 {
    @include throw.variable(
        "Must be greater than or equal to 1080.",
        "width", 
        $catch: false
    );
}
```

<h4>Global</h4>

```scss
$width: 1080;

@if $width < 1080 {
    @include variable-exception(
        "Must be greater than or equal to 1080.",
        "width",
        $catch: false
    );
}
```

<h2>License</h2>
<p><code>alapnian-sass</code> is under MIT License.</p>

<hr>

<p align="">
    <a target="_blank" title="Facebook" href="javasript:void(0)"><img height="15" alt="Facebook" src="https://img.shields.io/badge/-%231877F2.svg?style=badge&logo=Facebook&logoColor=white"/></a>
    <a target="_blank" title="Twitter / X" href="javasript:void(0)"><img height="15" alt="X" src="https://img.shields.io/badge/-%23000000.svg?style=badge&logo=X&logoColor=white"/></a>
    <a target="_blank" title="Instagram" href="javasript:void(0)"><img height="15" alt="Instagram" src="https://img.shields.io/badge/-%23E4405F.svg?style=badge&logo=Instagram&logoColor=white"/></a>
    <a target="_blank" title="Threads" href="javasript:void(0)"><img height="15" alt="Threads" src="https://img.shields.io/badge/-000000?style=badge&logo=Threads&logoColor=white"/></a>
    <a target="_blank" title="GitHub" href="javasript:void(0)"><img height="15" alt="GitHub" src="https://img.shields.io/badge/-%23121011.svg?style=badge&logo=github&logoColor=white"/></a>
    <a target="_blank" title="Mastodon" href="javasript:void(0)"><img height="15" alt="Mastodon" src="https://img.shields.io/badge/-%232B90D9?style=badge&logo=mastodon&logoColor=white"/></a>
    <a target="_blank" title="Pinterest" href="javasript:void(0)"><img height="15" alt="Pinterest" src="https://img.shields.io/badge/-%23E60023.svg?style=badge&logo=Pinterest&logoColor=white"/></a>
    <a target="_blank" title="Reddit" href="javasript:void(0)"><img height="15" alt="Reddit" src="https://img.shields.io/badge/-FF4500?style=badge&logo=reddit&logoColor=white"/></a>
    <a target="_blank" title="YouTube" href="javasript:void(0)"><img height="15" alt="YouTube" src="https://img.shields.io/badge/-%23FF0000.svg?style=badge&logo=YouTube&logoColor=white"/></a>
    <a target="_blank" title="LinkedIn" href="javasript:void(0)"><img height="15" alt="LinkedIn" src="https://img.shields.io/badge/linkedin-%230077B5.svg?style=badge&logo=linkedin&logoColor=white"/></a>
</p>
<p align="">
<small>
    Copyright 2025 <a href="https://alapnian.com/">Alapnian</a> — Developed by <a href="mailto:sass.dev@alapnian.com">Alapnian Sass Dev</a>
</small>
</p>