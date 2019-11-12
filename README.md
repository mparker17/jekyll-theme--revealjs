# jekyll-theme--revealjs

A minimalistic [reveal.js][revealjs] theme for [Jekyll][jekyll].

This theme loads the latest reveal.js from [CloudFlare's cdnjs service][cdnjs]. This means you have to be online when you load your slideshow for the first time, so if you anticipate spotty conference WiFi, you might want to do that ahead of time. You might also want to pin the tab or something so you don't close it accidentally.

Note this theme doesn't currently expose many of [reveal.js' configuration options][revealjs-config]. I hope to add more support for these over time.

[revealjs]: https://revealjs.com
[jekyll]: https://jekyllrb.com
[cdnjs]: https://cdnjs.com
[revealjs-config]: https://github.com/hakimel/reveal.js#configuration

# Why?

I created this project because:

1. I wanted to version control my slideshow,
2. I wanted a slideshow that I could load and use from any relatively modern device without transferring files, which meant a slideshow based on the near-universal HTML/CSS/JS standards,
3. GitHub does a pretty good job of version-controlling HTML/CSS/JS; and GitHub Pages does a pretty good job of hosting HTML/CSS/JS,
4. Reveal.js is a widely-used and frequently-updated HTML/CSS/JS slideshow framework that I've used before and found pretty nice,
5. I didn't want to clone/fork Reveal.js in my own repo because it would quickly get out of date, and it would clutter my repo with implementation details,
6. Existing Jekyll+Reveal.js solutions didn't work the way I wanted:
    * e.g.: they were based on Jekyll Plugins, which GitHub Pages doesn't let me use
    * e.g.: they assumed one Markdown file per slide, which was pretty intense
7. I wanted to use Markdown for the slide content if at all possible, since I find it much easier to work with than raw HTML
    * Both GitHub Pages and Reveal.js does this for me, but having Github do the rendering for me lowers the risk of accessibility tools running into Markdown and presenting something confusing to their users.
    * Plus, doing the Markdown-to-HTML conversion ahead of time reduces the work that the (potentially slow) presentation computer has to do.

# Install

There are [other ways to install and use themes][jekyll-themes], but the method presented here is the easiest way I've found to avoid cluttering your slides repo with implementation details.

1. Install [Ruby][ruby] with [rbenv][rbenv], [Bundler][bundler], and [GitHub Pages][github-pages], if you haven't already:

    ```bash
    $ rbenv install 2.4.1
    $ gem install bundler
    $ bundle init
    $ tee -a Gemfile <<'EOF'
    gem 'github-pages', '~> 202'
    EOF
    $ bundle install
    $ curl -o '.gitignore' https://raw.githubusercontent.com/github/gitignore/master/Jekyll.gitignore
    ```

2. Add the [benbalter/jekyll-remote-theme][benbalter-jekyll-remote-theme] plugin to `_config.yml`:

    ```yml
    plugins:
        - jekyll-remote-theme
    ```

    ... then run `bundle install`.

    Note that, because you made changes to `_config.yml`, you will need to restart `jekyll serve`

3. Use this project as your remote theme by adding a `remote_theme` line to `_config.yml`:

    ```yml
    remote_theme: mparker17/jekyll-theme--revealjs@master
    ```

    Note that, because you made changes to `_config.yml`, you will need to restart `jekyll serve`

4. You likely also want to set this theme's default layout (i.e.: `/_layouts/default.html`) as the default for all pages your repo (using [Front Matter Defaults][jekyll-front-matter-defaults]), so you don't have to manually specify the layout in the [front matter][jekyll-front-matter] of each file.

    To do this, add the following to `_config.yml`:

    ```yml
    defaults:
      -
        scope:
          path: ""
        values:
          layout: "default"
    ```

    Note that, because you made changes to `_config.yml`, you will need to restart `jekyll serve`

5. You likely want to add the [github/jekyll-commonmark-ghpages][jekyll-commonmark-ghpages] plugin so you can mix HTML (i.e.: to delimit slides) and Markdown (i.e.: for ease-of-use) more easily.

    To do this, add the following to `_config.yml`:

    ```yml
    plugins:
        - jekyll-commonmark-ghpages
    markdown: CommonMarkGhPages
    commonmark:
      options: ["SMART", "FOOTNOTES"]
      extensions: ["strikethrough", "autolink", "table", "tagfilter"]

    ```

    ... then run `bundle install`.

    Note that, because you made changes to `_config.yml`, you will need to restart `jekyll serve`

[jekyll-themes]: https://jekyllrb.com/docs/themes/
[ruby]: https://www.ruby-lang.org
[rbenv]: https://github.com/rbenv/rbenv
[bundler]: https://bundler.io
[github-pages]: https://github.com/github/pages-gem
[benbalter-jekyll-remote-theme]: https://github.com/benbalter/jekyll-remote-theme
[jekyll-front-matter-defaults]: https://jekyllrb.com/docs/configuration/front-matter-defaults/
[jekyll-front-matter]: https://jekyllrb.com/docs/front-matter/
[jekyll-commonmark-ghpages]: https://github.com/github/jekyll-commonmark-ghpages
