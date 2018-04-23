# Best Practice: CSS

Description
CSS, along with JavaScript and HTML, is a fundamental language of the web responsible for the presentation of websites. By presentation we mean everything from layout and positioning of elements to typography, colors, borders and backgrounds. Anything that changes the presentation of web content is (or should be) controlled with CSS.

## Specific Standards

One selector per line, with a space before the opening bracket

Yes:
```css
.selector1,
.selector2,
.selector3 {
    color: #ddd;
}
```
	
No:
```css
.selector1,.selector2,.selector3 {
    color: #ddd;
}
```

One property/value pair per line
	
Yes:
```css
.selector1 {
    display: block;
    margin: 0;
    padding: 0;
}
```

No:
```css
.selector1 {display: block; margin: 0;padding: 0;}
```

Closing bracket should be flush left with the same indentation as the opening selector.

As with all code, use consistent indentation. Either use the indentation used by other CSS in the product, or use 4-space indentation.

Don’t use IDs for styling, except where required by vendor systems or content management systems.

> From csswizardry.com: “They [IDs] have no advantage over classes (anything you can do with an ID, you can do with a class), they cannot be reused, and their specificity is way, way too high. Even an infinite number of chained classes will not trump the specificity of one ID.”


Use consistent ordering for properties. Configure your linting tool to help with this (example from Redux):

Display

```
display: block;
```

Positioning

```
position: relative;
```

Box model

```
margin: 0 10px;
padding: 5px;
```

Background

```
background-color: #eee;
background-image: url(‘../images/myawesomeimage.png’);
```

Border

```
border: solid 1px #eee;
border-radius: 3px;
```

Text

```
color: #ccc;
font-size: 1.2em;
```

Other

```
transition: all 0.2s ease;
```

## Commenting

Commenting is caring. Assume someone will come after you and need to quickly figure out what your CSS does, where various styles apply on the front end, etc.

```
In Sass files, prefer `// comments over `/* */` comments, because `/* */` comments may be rendered in the processed CSS. When using Sass, comments are not necessary in the processed CSS.
```

Use PHPdoc style comments as needed for larger, more descriptive comment blocks, but be aware that these comment blocks may be visible in the processed CSS.

## Preprocessors

Use of Sass for CSS preprocessing is encouraged.

When using Sass, the above best practices should be applied to the .scss code that you write, as the final CSS code will be generated by the preprocessor.

A linting tool like scss-lint to enforce best practices as you go is highly recommended. 


## Rationale

We want to create code that is high quality (see “Good Enough for Everyone” best practice), and that easy to maintain and work on collaboratively.

Code is communication.

Unlike scripting languages like JavaScript where a single missing character is likely to break something, CSS errors (like HTML errors) are generally well tolerated by web browsers, meaning that they will usually silently skip over errors and continue processing the rest of the CSS code. This fault tolerance is good for users in that a web page’s content will generally remain accessible even with poorly coded CSS. However, this also means that errors and poorly coded CSS can go unnoticed. 

CSS is a declarative language, meaning there it has none of the logic, variables, etc associated with programming languages such as JavaScript or PHP.  On the surface this makes CSS seem very simple, and it is easy to understand how CSS works. However, because of things like the cascading nature of CSS properties, inheritance, specificity, and the fault tolerance mentioned above, CSS can become very confusing and hard to debug.

While it may not be obvious to end users, poorly coded CSS can cause major problems for developers, especially in a team setting where others will be working with your code.

### A note on browser support

In 2013, developers adopted a policy on browser support to help prioritize reported bugs and inform browser testing for new code. That started here on ticket #913, and was finalized as:

#### Required

* IE11
* Edge
* Latest stable Chrome
* Latest stable Safari
* Latest stable Firefox

Test on touch devices, too. If you don't have one handy, use Browserstack (find our credentials in stache). Let’s at least support these mobile browsers:

* Latest stable Chrome on Android at phone and tablet sizes
* Latest stable Safari on iOS for iPhone and iPad


## Exceptions

3rd party code that is hard to touch, legacy projects that are near end of life.

## History

* 2014 October 16: Ratified
* 2015 January 26: Ginger added that we use a space before the opening bracket.
* 2015 June 24: Ginger added the browser support policy.
* 2016 October 12: Mike changed some formatting. Ginger added a linting example. Mike added the indentation standard. Mike and Ginger used Analytics to update the browser support policy.