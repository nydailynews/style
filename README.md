# Coding project style guide
Guidelines on code and coding projects for the NY Daily News newsroom.

## Commenting your code

A worthwhile comment explains to your future self a decision you made that you'd have to spend work figuring out otherwise. Look at commenting your code as explaining to your future self things in order to make your future self hate your past self and your past self's decisions less.

A good comment doesn't re-tell what's already immediately obvious in the code. In order for this to work, the elements of the code ([such as variable, function and class names](#variable-function-and-class-names)) should have names that communicate what those elements are about.

More reading about code comments: [Code Tells You How, Comments Tell You Why](https://blog.codinghorror.com/code-tells-you-how-comments-tell-you-why/)

## Religious battles

### Spaces vs. tabs

Spaces, four of them.

### CamelCase vs. underscore_each_word

Underscores, please. The one exception: When naming classes, use camelCase.

## Other naming conventions

### File and directory names
Naming files and directories consistently will make certain things in your world a little bit easier.

Some basics:
* All names should be lower-case, always. Keeping file and directory names lower-case makes one less thing you have to think about when typing in URLs and when creating file / directory names.
* Use hyphens in directories, use underscores in file names. Never use spaces.
* Keep directory names for directories that store assets as short as can be while still being clear.
* Image file names should be as clear as possible. If the image is a photo, make sure you can tell what the photo is of from the file name.
* For sites and projects that have one file with a bunch of custom javascript in it, call that file `app.js` for the sake of consistency.

### Variable, function and class names

Regarding style, see [camelCase vs. underscores](#camelcase-vs-underscore_each_word).

Regarding what makes a communicative variable name: Nouns are a start. If your variable is an array of records from a CSV, `rows` or `records` is a good place to start. Don't be too specific. `rows` works as long as there's not another something clamoring to be named `rows` too -- if there is, go the `rows_[some other noun]` route rather than the `rows2` route. Putting numbers in a variable name is usually a sign something's wrong.

#### Function & class names

#### CSS id & class names

#### Constant names

Constants act like a variable but once a constant is set it doesn't change. Often these are used as environment vars used to configure a particular app on a particular server / computer. Constants have an explicit place in PHP and environment vars have a defined place in the shell, and this ALLCAPS style can be used in Python and Javascript with no side effects.

Constant names should be UPPERCASE_WITH_UNDERSCORES.

### What about when I'm importing code that uses its own style?

Let it be and cite the source in the comments, if appropriate.

## HTML style

Markup should be readable when viewed. Also, when stylesheets are disabled, the markup of the document should still make sense.

### When to add classes, when to add id's, and when to use markup

## Javascript style

Writing a bunch of functions with loose javascript in between is the enemy. Organizing your javascript into discrete objects is a solid first step toward code maintainability and test-ability. I would write more but [Clean Code: Javascript](https://github.com/ryanmcdermott/clean-code-javascript) has already written it. Read that.

## CSS style

Four-space tabs, if it's a one-line declaration keep it on one line, ala
```css
ul.emphasis li { font-size: 4em; }
```
Otherside declare styles like
```css
article > p {
    line-height: 1em;
    color: #333;
}
```

## Python style

[PEP8 is the Python style guide and is worth reading](https://www.python.org/dev/peps/pep-0008/).

## PHP style

### Braces and if / foreach / loop syntax

PHP lends itself to piles of hard-to-decipher close-braces. Here are some preferred techniques to avoid tag soup:

#### if / endif

Instead of `if ( clause ) { some_code(); }`, do `if ( clause ): some_code(); endif;`. Same for `foreach`'s.

## Project management

### Committing to repo

#### When to commit

Commit early and often. You don't need to push with every commit, but incremental commits will allow you to retrace the decisions you made should you need to do that.

#### How to write an adequate commit message

Start your commit message with a verb. Describe what changed. If you made a decision you'd like to remember later, mention that and explain it.

Bad commit message:
```
It's fixed.
```

Better commit message:
```
Fixed the inaccurate markup in index.html.
```

Best commit message:
```
Fixed the inaccurate markup in index.html. Using <p>'s instead of <br>'s improves the document's accessibility.
```

### Creating repositories vs. creating snippets vs. other technical writing things

Are you writing a reference document or how-to that's not attached to a particular code repo? Write it in markdown and make it a public gist ([example](https://gist.github.com/freejoe76/06544a90fd14183acd43f5812d3b933b)).

Are you writing a snippet of code (HTML, JS, whatever) for someone else to use? Don't email it, put it in a gist and send the person a link with clear intstructions. ([example gist](https://gist.github.com/freejoe76/363821580ff523062ffbde3fe4aa54b1)).

#### How to lay out a project repo

Vanilla projects get a:

* `README.md`
* `requirements.txt` for projects that use python and need a virtualenv.
* `www/` directory
* `www/js/`, `www/css/`, `www/img/`, if necessary

If this is a project that will have an index as well as indvidual URLs ([such as the quiz project](http://interactive.nydailynews.com/quiz/), also create a `_blank` directory inside the `www` directory. In there store the template files for an individual thing, whatever that thing is you're publishing (a single quiz, a single longform, etc.).

When a project is based on a particular framework such as flask or django, different project layouts may be required.

### When to use a database vs. when to not use a database

Most of the time you don't need a database for your project. Even many of the times you think you need a database, you don't. Places you might need a database include interactives that record user data (though you don't always need a db for that), gigantic multi-join table situtations, you have a data dump in sql format, you want to try sqlite out for something and you promise it won't become a deal.
