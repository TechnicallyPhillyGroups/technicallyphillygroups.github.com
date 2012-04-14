# Web page for TechnicallyPhillyGroups.org

This site uses the following technologies:

* [Twitter Bootstrap][]
* [Sass-Twitter-Bootstrap][], which contains [Sass][] ports of Twitter's
  [Less][] CSS files.
* [Sass][]
* [Ruby][]
* [Jekyll][]
* [Rake][]
* [Bourbon][]

Twitter Bootstrap is already folded into the project, though it can be
customized and updated. Bourbon is also folded into the project, but you'll
need to install the gem. (See next step.)

## Before you build for the first time

First, install a version of Ruby 1.9. (I've been using 1.9.3, via [rvm][].)
Then, install the `bundler` gem:

    $ gem install bundler

Have `bundler` install everything else, courtesy of the `Gemfile` in this
directory:

    $ bundle install

## Building the web site

Use Rake. Don't invoke Jekyll directly, because there are other tasks to be
done, tasks that Jekyll can't do (especially on GitHub, where the web site is
hosted).

It's best to use `bundle exec` to run `rake` in a controlled environment (as
dictated by `Gemfile`):

    $ bundle exec rake

## To preview your changes

Run

    $ bundle exec rake preview

Then, surf to `localhost:4000`.

## Publishing

To publish the site to GitHub, *always* run Rake first. Here are the steps:

    $ bundle exec rake 
    $ git commit -am 'your commit message'
    $ git push origin gh-pages

To push to the GitHub repository, you'll need two things:

1. A GitHub account.
2. Permission to push to the repository. Contact [André Dhondt][] or
   [Brian Clapper][] to request permission to push.

[Brian Clapper]: https://github.com/bmc
[André Dhondt]: https://github.com/adhondt

## Styling

### To customize the look and feel

Customize `sass/styles.scss`. Then, rebuild the site. Note that this file
is a [Sass][] input file, so edit accordingly.

Twitter Bootstrap customization is also controlled in `styles.scss`, courtesy
of [Sass-Twitter-Bootstrap][]. The Twitter Bootstrap LESS variables that are
documented on the  [Twitter Bootstrap][] web site are available as Sass
variables, inside `styles.scss`. For example, the LESS variable `@navbarHeight`
is `$navbarHeight`, inside the Sass file. The names are the same, but the
syntax is pure Sass.

## Updating Twitter Bootstrap and Sass-Twitter-Bootstrap

To update the installed files from Twitter Bootstrap and Sass-Twitter-Bootstrap
(e.g., to pick up some bug fixes), run this Rake command:

    $ bundle exec rake bootstrap

That command will

* Clone the Twitter Bootstrap repo (the master) into a temporary directory.
* Copy the appropriate files from the cloned repo to the `./bootstrap`
  directory, if they've changed.
* Compile all Bootstrap Javascript files into minified versions, storing the
  results in `./bootstrap/js`.
* Create `./_includes/bootstrap.js.html`, which pulls in the Bootstrap
  Javascript
* Clone the Sass-Twitter-Bootstrap repo into a temporary directory.
* Copy the appropriate Sass files from the cloned repo into the
  `./bootstrap/sass` directory.

[Less]: http://lesscss.org/
[Twitter Bootstrap]: http://twitter.github.com/bootstrap/
[Bourbon]: http://thoughtbot.com/bourbon/
[Jekyll]: http://jekyllrb.com/
[Sass-Twitter-Bootstrap]: https://github.com/jlong/sass-twitter-bootstrap
[Sass]: http://sass-lang.com
[Rake]: http://rake.rubyforge.org/
[Ruby]: http://ruby-lang.org/
[rvm]: http://rvm.beginrescueend.com/
