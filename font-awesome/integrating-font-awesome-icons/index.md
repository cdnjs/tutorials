# How to integrate font-awesome icons in your site.

The Font-Awesome project provides tons of useful icons you can use to improve your site!

## Why Font-Awesome?

Font-Awesome provides multiple icons for deveopers to use in their webpages and webapps. Icons can help users more easily navigate your site. You don't have to speak English to guess what the back button might do.

## Getting started

Font-Awesome is incredibly easy to work with. Here's our ultra simple happy page:

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8">
        <title>Happy Page</title>
        <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.4.0/css/font-awesome.min.css" rel="stylesheet">
        <link href="https://cdnjs.cloudflare.com/ajax/libs/twitter-bootstrap/3.3.5/css/bootstrap.min.css" rel="stylesheet">
    </head>
    <body>
        <button type="button" class="btn btn-default btn-lg" onClick="smile()"> Happy Button </button>
        <script>
            function smile() {
                alert("Don't worry, be happy! Smile, it's free!");

            }
        </script>
    </body>
</html>
```

Our happy page consists of a simple bootstrap button that when pressed, reminds us smiling is free.

But adding a smiley-face to the happy button would make it so much happier. Here's how font-awesome icons work.

## How Font-Awesome Icons are Integrated

```html
<i class="fa fa-smile-o"></i>
```

That is the code block for the smiley icon. Inserting it anywhere in your page will allow cause the smiley to appear. Under the class value you place the font-awesoke default class "fa" and the icon's id;

All font-awesome icons and their id's can be found here:

[http://fortawesome.github.io/Font-Awesome/icons/](http://fortawesome.github.io/Font-Awesome/icons/)

Infact, the site even gives you the entire icon code block to use!

## Integrating the icon into our button

Placing the icon into our button is a simple as pasting the code block where we want in the button's text value. It would result like so:

```html
<button type="button" class="btn btn-default btn-lg" onClick="smile()"><i class="fa fa-smile-o"></i> Happy Button <i class="fa fa-smile-o"></i></button> 
```

As you can see, you can have as many icons as you want. For the example we use two smiley faces. The resulting Happy page would be this:

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8">
        <title>Happy Page</title>
        <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.4.0/css/font-awesome.min.css" rel="stylesheet">
        <link href="https://cdnjs.cloudflare.com/ajax/libs/twitter-bootstrap/3.3.5/css/bootstrap.min.css" rel="stylesheet">
    </head>
    <body>
        <button type="button" class="btn btn-default btn-lg" onClick="smile()"><i class="fa fa-smile-o"></i> Happy Button <i class="fa fa-smile-o"></i></button>
        <script>
            function smile() {
                alert("Don't worry, be happy! Smile, it's free!");

            }
        </script>
    </body>
</html>

```

And there we have it! Our Happy Page just became a really haply page! Font-Awesome icons don't only make sites easier to work with. A right use of icons will add a nice finished touch to your page, especially on mobile devices! It minimizes your need to use words (eww, words) and opens it those with reading disabilities and such!

So armed with your package of icons, its time to go polish your web projects! Good luck!

### Contributors

* [lite20](https://twitter.com/lightningboy24) (created integration tutorial
