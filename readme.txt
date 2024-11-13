How to build this site:

Everything in _site is temporary and gets overwritten when the site is rebuilt. Keep this in mind and don't bother editing it.

This site uses Jekyll, which in turn uses Ruby (a packaging thing), Liquid (a way to make variables work in the pages, and probably some other stuff I don't understand. To learn more about Jekyll, this is where all the good info is `https://jekyllrb.com/docs/`. The key thing about Jekyll is that it's what github pages uses.

To build and run, enter `bundle exec jekyll serve`. This starts a server, which occupies the terminal tab, which is probably okay since you want to preserve ctrl+c to kill the server. To access the site, go to `http://localhost:4000`.

bundle exec jekyll serve --livereload
This command will cause refreshes when you update stuff.

The Gemfile is where the packaging and versioning stuff happens. When edited, it's good to run `bundle install` to update all the versions. Gemfile.lock looks like an auto-generated thing from the Gemfile which includes all the dependencies.


These sites have themes, which is really just a bunch of default behaviour that exists until overwritten. This one probably is using minima, which is defined here: https://github.com/jekyll/minima/blob/master/

It's also defined here: /Users/markmccarthy/.gem/ruby/3.1.3/gems/minima-2.5.1/
