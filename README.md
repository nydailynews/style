# Coding project style guide
Guidelines on code and coding projects for the NY Daily News newsroom.

## Commenting your code

A worthwhile comment explains to your future self a decision you made that you'd have to spend work figuring out otherwise. Look at commenting your code as explaining to your future self things in order to make your future self hate your past self and your past self's decisions less.

A good comment doesn't re-tell what's already immediately obvious in the code. In order for this to work, the elements of the code ([such as variable, function and class names](#variable-function-and-class-names)) should have names that communicate what those elements are about.

More reading about code comments: [Code Tells You How, Comments Tell You Why](https://blog.codinghorror.com/code-tells-you-how-comments-tell-you-why/)

## Religious battles / things some people feel strongly about

### Spaces vs. tabs

Spaces, four of them.

### Hyphens vs. underscores

On the frontend (CSS / HTML), if there's a chance whatever it is you're naming could end up in a URL, use hyphens.

### CamelCase vs. underscore_each_word

Underscores, please. The one exception: When naming classes, use camelCase.

### Single vs. double quotes

Single quotes are faster to type, so unless you've got a reason to use double quotes, use singles.

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

Class names are the exception to the use underscore rule of naming things. Make class names camel case.

#### Constant names

Constants act like a variable but once a constant is set it doesn't change. Often these are used as environment vars used to configure a particular app on a particular server / computer. Constants have an explicit place in PHP and environment vars have a defined place in the shell ([more about environment vars and the shell here](https://github.com/Idnan/bash-guide#a-export)), and this ALLCAPS style can be used in Python and Javascript with no side effects.

Constant names should be UPPERCASE_WITH_UNDERSCORES.

### What about when I'm importing code that uses its own style?

Let it be and cite the source in the comments, if appropriate.

## HTML style

Markup should be readable when viewed. Also, when stylesheets are disabled, the markup of the document should still make sense.

### When to add classes, when to add id's, and when to use markup in layout
High level overview: Stick to markup elements as much as possible, save classes for situations when a particular element needs to be differentiated and id's for situations where one particular element will be manipulated with javascript or could be linked to in the page directly.

## Javascript style

Writing a bunch of functions with loose javascript in between is the enemy. Organizing your javascript into discrete objects is a solid first step toward code maintainability and test-ability. I would write more but [Clean Code: Javascript](https://github.com/ryanmcdermott/clean-code-javascript) has already written it. Read that.

## CSS style

Declare styles like
```css
article > p {
    line-height: 14px;
    color: #333;
}
```

*Use pixels for everything* ([Why](https://benfrain.com/just-use-pixels/), also [why](https://hackernoon.com/rems-and-ems-and-why-you-probably-dont-need-them-664b9ce1e09f)).

### CSS id & class names

Use hyphens in class and id names, hyphens are easier to type and sometimes id's are used in permalinks, in which case you definitely don't want to have to be thinking "should this be an underscore or a hyphen"?

### Things to avoid in your CSS

1. Avoid colors or numbers in class and id names.
2. [Magic numbers](https://css-tricks.com/magic-numbers-in-css/)

## Python style

[PEP8 is the Python style guide and is worth reading](https://www.python.org/dev/peps/pep-0008/).

For a boilerplate Python 2 file, [you could do worse than this](https://gist.github.com/freejoe76/7af5a3d88766f3ae6fa0c77bacaa002a).

## PHP style

### Braces and if / foreach / loop syntax

PHP lends itself to piles of hard-to-decipher close-braces. Here are some preferred techniques to avoid tag soup:

#### if / endif

Instead of `if ( clause ) { some_code(); }`, do `if ( clause ): some_code(); endif;`. Same for `foreach`'s.

## Project management

###  Code repositories

We store code on Github and on Bitbucket. Use Bitbucket for endeavors that need to be private and for project-specific repos, use Github for everything else. Example: Keep 'Em Dump 'Em and its template / app files are stored on Github, but individual Keep 'Em Dump 'Ems are stored on Bitbucket.

#### When to commit

Commit early and often. You don't need to push with every commit, but incremental commits will allow you to retrace the decisions you made should you need to do that.

Note: If you're starting a project, you don't even have to attach it to a repo. `git init` in your project's directory will allow you to make commits against a project, once you know where the project's repo lives you can connect the two with a command such as `git remote add origin ssh://git@bitbucket.org/nydailynews/fiction.git`.

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

### Handling project-specific configuration variables

Hard-coding things into the project that have to be changed when the project is launched makes it hard to launch and hard for others to collaborate with you on your project. You can avoid some of this with relative paths on HTML src / href's. Sometimes, in other situations, it's unavoidable and you have to create a variable to handle a project-specific configuration thing.

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

## On debugging

### Debugging JS

If you want to see all the JS that's on a particular URL, head over to Firefox, get the [Web Developer Toolbar](https://addons.mozilla.org/en-US/firefox/addon/web-developer/) (the Chris Pedrick one, it's a classic), load the URL and go to information --> View Javascript. This is good for figuring out all the javascript that's working on a particular element / variable / finding all the scroll handlers clogging up a particular page.

### Debugging CSS

https://css-tricks.com/debugging-tips-tricks/

### Debugging cross-browser issues

[View how it looks in Internet Explorer here](https://netrenderer.com/)

### Debugging handheld issues

## Resources

Links that might be useful for whatever reason.

* Zed Shaw's [Command Line Crash Course](https://learnpythonthehardway.org/book/appendixa.html)
