# SASS

> **Sass ⇒** Syntactically awesome style sheet. It is an extension of CSS. Sass was designed by Hampton Catlin and developed by Natalie Weizenbaum in 2006.

> Sass has some extra special features that do not exist in CSS like: 1. variables 2. nested rules 3. mixins, imports 4. inheritance

> **Purpose ⇒** to make our code simpler and more maintainable. No dry(we can @extend CSS rules). free to download. It supports all versions of CSS

> SASS code(demo.scss) ⇒Pre-Processor(transpiler) ⇒ Standard CSS code(demo.css) ⇒ browser

> Install **live sass compiler extension** in vscode: 1. create a styles folder ⇒ demo.scss ⇒ add some code into it 2. <link rel =”stylesheet” href=”./styles/demo.css” /> 3. start watching sass by clicking watch sass

> Sass supports 2 types of comments. 1. standard CSS comments /_ comment _/ 2. Inline comments // comment

> **Sass variables: sass variable is more simpler than CSS variables that we have used already.** Like js(let, const) we can start declaring the variable using $

                                                                                                 **Example:**                                                                                       declaring :                                                                              $header-bgcolor: colorName;                                                      $main-bgcolor: colorName;                                                    $para-fontsize:size;

**Using:**

> header{ Background: $header-bgcolor ; }

> Using Sass variables we can store:

> 1. strings 2. numbers 3. colors 4. booleans 5. lists 6. nulls

**index.html ⇒**

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Sass Learning</title>
    <link rel="stylesheet" href="./styles/demo.css" />
  </head>
  <body>
    <header>
      <h1>Study with Swarna</h1>
    </header>
    <nav>
      <ul>
        <li><a href=""></a>Home</li>
        <li><a href=""></a>Contact</li>
        <li><a href=""></a>About us</li>
      </ul>
    </nav>
    <main>
      <section id="about">
        <h2>About</h2>
        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Laborum,
          dignissimos qui totam molestiae dolores hic! Voluptatem nemo autem
          provident nisi, doloribus consectetur similique expedita nulla atque
          hic commodi quam! A.
        </p>
      </section>
    </main>
    <footer>
      <p>copyright &copy; studywithswarna</p>
    </footer>
  </body>
</html>
```

**demo.scss**

```scss
// color variable declaration
$header-bgcolor: #ffab73;
$main-bgcolor: #ffd384;
$footer-bgcolor: #ffaec0;

$para-fontsize: 15px;

//  nav styling
//using sass

// using nesting
nav {
  margin-top: 15px;
  ul {
    list-style-type: none;
    li {
      display: inline-block;
      margin: 5px 15px;
      a {
        text-decoration: none;
        display: inline-block;
        padding: 10px;
        transition: 0.4s;
        border-radius: 5px;
      }
      a:hover {
        background: #000;
        color: white;
      }
    }
  }
}
// using css
nav {
  margin-top: 15px;
}

// nav ul{
//     list-style-type: none;
// }
// nav ul li{
//     display: inline-block;
//     margin: 5px 15px;
// }
// nav ul li a{
//     text-decoration: none;
//     display: inline-block;
//     padding: 10px;
//     transition: 0.4s;
//     border-radius: 5px;

// }
// nav ul li a:hover{
//     background: #000;
//     color: white;

// }

/*browser reset code
 */

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
header {
  background: $header-bgcolor;
}
main {
  background: $main-bgcolor;
}
#about p {
  font-size: $para-fontsize;
}
footer {
  background: $footer-bgcolor;
}
```

> **Partials⇒**
>
> What are partials in Sass?
>
> Sass PartialsBy default, Sass transpiles all the .scss files directly. However, when you want to import a file, you do not need the file to be transpiled directly. Sass has a mechanism for this: **If you start the filename with an underscore, Sass will not transpile it**. Files named this way are called partials in Sass.

**index.html ⇒**

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <link rel="stylesheet" href="./dist/main.css" />
  </head>
  <body>
    <header>
      <h1>Sass Project</h1>
    </header>
    <main>
      <h2>About</h2>
      <p>
        Lorem ipsum dolor sit, amet consectetur adipisicing elit. Nam vero
        eaque, perferendis natus nesciunt est et porro distinctio sequi autem?
      </p>
    </main>
  </body>
</html>
```

scss/**main.scss: ⇒ inside scss folder file name main.scss**

```scss
// @forward "./base/reset"; // for accessing reset file inside base folder
// @forward "./base/typography";  // if we want to access some style but not acess any variable then we use @forward

@forward "./base/index"; //inside base folder inside index.scss file we use all partials for using one time
// @use "./util/index";  // if we want to access any value or variable from another file then we will use @use
@use "./util/index as variable"; // we can rename file by using as
header {
  // background-color: index.$header_bg;  // we have to use fileName.$variableName
  background-color: variable.$header_bg;
  padding: 1rem;
}
main {
  background-color: index.$main-bg;
  padding: 1rem;
}
```

**scss/base/\_index.scss ⇒**

```scss
@forward "reset";
@forward "typography"; // we use forward for using reset and typography file
```

**scss/base/\_reset.scss ⇒**

```scss
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  list-style-type: none;
  text-decoration: none;
  outline: none;
}
```

**scss/base/\_typography.scss ⇒**

```scss
h1,
h2 {
  margin-top: 0;
  color: purple;
}
```

**scss/util/\_index.scss ⇒**

```jsx
@forward "variables”
```

**scss/util/\_variable.scss ⇒**

```scss
$header_bg: #ffe4c4;
$main-bg: aquamarine;
```

> we will use util/utilites folder for accessing variable and base folder for using any default styles.

> **mixin⇒ a group of CSS declarations that can be reused throughout the style sheet.**

```jsx
@mixin para-style{
 font-size: 16px;
	text-align: justify;
}
```

```jsx
#about-me p{
	@include para-style; // using mixin by @include
}
```

> **extend⇒** we can inherit one selectors property to another selector.

```scss
.btn {
  border: none;
  padding: 15px 30px;
  text-align: center;
  font-size: 16px;
  cursor: pointer;
}
.btn-download {
  @extend .btn;
}
```

**if, else — if, else⇒**

```scss
@mixin setFontSize($value) {
  @if $value == small {
    font-size: 12px;
  } @else if $value == medium {
    font-size: 16px;
  } @else {
    font-size: 20px;
  }
}
```

access⇒

```scss
a {
  @include setFontSize(small);
}
```

**loop⇒ as like JS**

> @for $i from 1 through 12{ // do something }

> 2 ways to declaration⇒ 1. start through end(it includes end number) 2. start to end(does not include end number)

```scss
[class*="col-"] {
  float: left;
}
// .col-x{width: x%;}
// .col-x{width: 100% /12;}
// .col-1 {width: 8.33%;}
// .col-2 {width: 16.66%;}
// .col-3 {width: 25%;}
// .col-4 {width: 33.33%;}
// .col-5 {width: 41.66%;}
// .col-6 {width: 50%;}
// .col-7 {width: 58.33%;}
// .col-8 {width: 66.66%;}
// .col-9 {width: 75%;}
// .col-10 {width: 83.33%;}
// .col-11 {width: 91.66%;}
// .col-12 {width: 100%;}

//for loop

@for $i from 1 through 12 {
  .col-#{$i} {
    width: 100% / 12 * $i;
  }
}
.row::after {
  clear: both;
  content: "";
  display: table;
}
```

```scss
// while loop
$i: 1;
@while $i<13 {
  .col-#{$i} {
    width: 100% / 12 * $i;
  }
  $i: $i + 1;
}
```

**map⇒**

> .red-text{color:red}
> .green-text{color:green}
> .blue-text{color:blue}
> .black-text{color:black}

```jsx
@each $color in red,green,blue,black
{
	.#{$color}-text{color:$color;}
}
```

```jsx
$colors:(color1:red, color2:green, color3:blue);
@each $key, $color in $colors{
		.#{$color}-text{
		color: $color;
   }
}
```
