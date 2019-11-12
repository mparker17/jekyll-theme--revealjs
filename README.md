# jekyll-theme--revealjs

A minimalistic [reveal.js][revealjs] theme for [Jekyll][jekyll].

This theme loads the latest reveal.js from [CloudFlare's cdnjs service][cdnjs]. This means you have to be online when you load your slideshow for the first time, so if you anticipate spotty conference WiFi, you might want to do that ahead of time. You might also want to pin the tab or something so you don't close it accidentally.

Note this theme doesn't currently expose many of [reveal.js' configuration options][revealjs-config]. I hope to add more support for these over time.

[revealjs]: https://revealjs.com
[jekyll]: https://jekyllrb.com
[cdnjs]: https://cdnjs.com
[revealjs-config]: https://github.com/hakimel/reveal.js#configuration

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

4. You likely also want to set this theme's default layout (i.e.: `/_layouts/default.html`) as the default for all pages your repo, so you don't have to manually specify the layout in the front-matter of each file. To do this, add the following to `_config.yml`:

    ```yml
    defaults:
      -
        scope:
          path: ""
        values:
          layout: "default"
    ```

    Note that, because you made changes to `_config.yml`, you will need to restart `jekyll serve`

[jekyll-themes]: https://jekyllrb.com/docs/themes/
[ruby]: https://www.ruby-lang.org
[rbenv]: https://github.com/rbenv/rbenv
[bundler]: https://bundler.io
[github-pages]: https://github.com/github/pages-gem
[benbalter-jekyll-remote-theme]: https://github.com/benbalter/jekyll-remote-theme
