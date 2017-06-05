# Netflix Clone

## Introduction

## HTML and CSS

We'll be creating Web pages with HTML and CSS. So, what are they you might ask? Well, all you need to know at this point is that HTML (or Hypertext markup language) is what you use to structure the content of your site that browsers can understand. Think of all the headings, paragraphs and links to other pages you see on the sites. CSS (or Cascading Style Sheets) is what you use to style appearance of the content created by HTML. Think of such things as colors of the texts, animations, and typography.

## Writing your first HTML page

To begin writing your first HTML page, all we need is a text editor and a Web browser. I am a big fan of [Atom](https://atom.io/) editor provided by [GitHub](https://github.com).

Let's create a new file and save it with *.html* extension, similarly to *.doc* used by Microsoft Word.

Now, all HTML documents are required to have a certain structure that include the following declaration and elements.

    <!DOCTYPE html>
    <html>
      <head>
      </head>

      <body>
      </body>
    </html>

Let me explain it to you line-by-line:

* `<!DOCTYPE html>` tells the browser the version of HTML we'll be using. In this case, though we're just saying we're going to use  the latest version available.

* `<html>` tells that we're a starting a new HTML document. By the way, these identifiers (or elements) enclosed in `<` and `>` are called tags. There are different kind of tags, such as headings, paragraphs, links, etc. Here we say we're starting an HTML document and down there we're ending it with `</html>`. Most of the tags have to be closed, except to a few we will see later.

* Inside the HTML document, we specify the so called `<head>` tag, which is used as the top of the document for it's title, links to other resources, and other metadata. This section is processed by the browser, but not visible to the users.

* Finally, we have the `<body>` tag, which defines what will be visible to the users looking at this page.

Now save the file and open it in the browser. Nothing interesting, right?

Let's add some more tags:

      <head>
        <meta charset="utf-8">
        <title>Netflix Spain - Watch TV Shows Online, Watch Movies Online</title>
      </head>
      ...
      <body>
        <h1>See what's next.</h1>
      </body>
  
* Firstly, we'll add the `<title>` of the page just like on the Netflix site.
* Then, we'll add the `<meta>` tag defining the character encoding of this document, so that the browser would know how to show special characters in different languages.
* Finally, we'll extend the `<body>` section with something interesting for the users, the main heading `<h1>` as on the Web site.

## Writing your first CSS

The page looks very dull, so let's add some appearance to it with CSS. As mentioned earlier, the HTML `<head>` section is used to link to any additional resources, and that's exactly where we'll link to our CSS file.

        <link href="css/style.css" rel="stylesheet"/>
        

* `href` is an attribute of the `<link>` tag, which says where to look a CSS file.
* So, this would search for a file named `style.css` in the `css` directory relative to our html file. As you see, CSS has it's own extension `.css`.
* The `rel` attribute denotes that we're linking *stylesheet*, and not icons, or anything else. 
* Create a `css` directory with a `style.css` file:

    body {
      margin: 0;
    }

* In CSS we target elements we want style. Each definition is wrapped into a pair of curly braces and every statement inside is terminated with a semicolon.
* In the example above, we target `body` element and remove any space around it with a CSS property named `margin`.

Next up, let's add a background image to the page into a so called *header* section.

    <header>
      <h1>See what's next.</h1>
    </header>

* `<header>` is an HTML tag that represents a container for an introductory content or navigational links.
* Back to CSS and set the background image to the header:

    header {
      background-image: url('../img/header-background.jpg');
      height: 100vh;
    }

* The `background-image` property sets a background for an element  at a given location.
* The `height` property will set the header to `100vh`, which means 100% of viewport height, where viewport is the screen.

## Adding navigation and logo with SVG

Let's add page navigation with a Netflix logo next.

    <nav>
      <a href="">Netflix</a>
    </nav>
    

So, this was our first link inside a `<nav>` tag, which defines the navigational items on the page. In contrast to `link`'s `href` attribute, here we could link to another page. For example, we could have a page named `about.html` and link to it, however leaving it empty make we could make it always point to the current page.

Now let's replace the text with an actual Netflix logo. And for that we'll use a new tag, called `<img>`.

    <a href="">
      <img src="img/logo.svg">
    </a>  

As you see, `<img>` tag has an attribute `src` that links to an actual image. But it's too big, so we'll make it the same size as on the original page. Notice how we nest the `img` element in CSS inside the `nav` element, because we don't want other images on the page to get these properties.

    nav img {
      width: 167px;
      height: 45px;
    }

We'll make a few more adjustments to the position of the logo and navigation. First of all, we'll define a class for an `<a>` tag so that we can reference it in CSS and set the height to the navigation.

    <a class="logo" href="">

And CSS:

    nav a {
      display: inline-block;
      line-height: 90px;
    }
    
    header nav {
      height: 90px;
    }
    
    nav img {
      max-width: 167px;
      max-height: 45px;
      vertical-align: middle;
    }
    
    nav .logo {
      margin-left: 3%;
    }

* The `display` property specifies the box type for an element. The box model is a CSS concept of how elements are positioned on the page.
* Then we set the height of the `<a>` tags inside navigation to 90px.
* Then we align the image inside the navigation vertically in the middle.
* And finally, add 3% left spacing to our link with a class `.logo`.

Finally, let's add the *Sign in* button to the navigation on the right:

    <a class="signin" href="https://www.netflix.com/login">
      Sign In
    </a>
    
    nav .signin {
      color: #fff;
      float: right;
      background-color: #e50914;
      line-height: normal;
      margin-top: 18px;
      margin-right: 3%;
      padding: 7px 17px;
      font-weight: 400;
      border-radius: 3px;
      font-size: 16px;
      text-decoration: none;
    }

* This time we've linked to an external page and defined the class for this link `signin`, which we can use further in CSS.
* Notice the color codes are in the so called [HEX format](http://htmlcolorcodes.com/).
* The `float` is a new property that tells the element to be positioned on the right.

## Adding fonts and default styles

The fonts do not look similar to ones on the Netflix site, so let's add them to be applied to entire page, as well as the default font size and colors:

    html, body {
      font-family: 'Helvetica Neue',Helvetica,Arial,sans-serif;
      color: white;
      background-color: black;
      font-size: 16px;
      margin: 0;
    }

Notice how we can target multiple elements in CSS by separating them with a comma. The `font-family` sets the font for the texts on the page.

## Adding pitch section

Now, we'll add the pitch area.

    <section class="pitch">
      <h1 class="pitch__title">See what’s next.</h1>
      <p class="pitch__subtitle">WATCH ANYWHERE. CANCEL ANYTIME.</p>
    </section>

* As you see, we've used the new `<section>` tag to define the section of the page and gave it a class `pitch`. This allows us to work with these elements as a group in CSS.
* We also introduced a `<p>` tag, which is just a paragraph.
* We also gave the classes to `<h1>` and `<p>` tags, prefixing them with the class of a section for better reading.

    .pitch {
      margin: 0 3%;
      position: absolute;
      top: 35%;
      font-size: 1.8vw;
    }

    .pitch__title {
      font-size: 3em;
      margin: 0 0 0.2em;
      font-weight: 700;
    }

    .pitch__subtitle {
      margin: 0 0 .5em;
    }

* This is another way of specifying `margin`. Instead of defining each margin (`margin-right`, etc.), we only set one margin for values top, right, bottom, left. Alternatively, we could condense it further and set the first value for both top and bottom, which is 0, and the second part for left and right, which is 3% as with the logo.
* `position` property specifies the positioning method used. It's used in conjunction with `top` property, which says to have 35% from the top of the page.
* `font-size` is defined in [viewport units](https://css-tricks.com/viewport-sized-typography/), telling to use 1.8% of viewport width.

## Adding JOIN button and hover effects

Next up, we'll add JOIN button with a new `button` tag:

    <p class="pitch__subtitle">...
    <button class="btn">JOIN FREE FOR A MONTH</button>

And a corresponding CSS:

    .btn {
      font-size: 14px;
      letter-spacing: 1.9px;
      font-weight: 400;
      margin: .5em .5em .5em 0;
      padding: 12px 2em;
      color: #fff;
      background-color: #e50914;
      cursor: pointer;
      text-decoration: none;
      vertical-align: middle;
      font-family: Arial,sans-serif;
      border-radius: 2px;
      user-select: none;
      text-align: center;
      border: 0;
    }    

How about adding hover effects, meaning when you mouse over the buttons? Well, we have an `:hover` selector that can be applied to the elements, so let's add it to the both buttons we have:

    nav .signin:hover, .btn:hover {
      background: #f40612;
    }  

