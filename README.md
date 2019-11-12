# jekyll-theme--revealjs

A minimalistic [reveal.js][revealjs] theme for [Jekyll][jekyll].

[revealjs]: https://revealjs.com
[jekyll]: https://jekyllrb.com

# Install

1. Install [Ruby][ruby] with [rbenv][rbenv], [Bundler][bundler], and [Github Pages][github-pages], if you haven't already:
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

Note there are [other ways to install and use themes][jekyll-themes], but the method above is the easiest way to avoid cluttering your slides repo with implementation details.

[ruby]: https://www.ruby-lang.org
[rbenv]: https://github.com/rbenv/rbenv
[bundler]: https://bundler.io
[github-pages]: https://github.com/github/pages-gem
[benbalter-jekyll-remote-theme]: https://github.com/benbalter/jekyll-remote-theme
[jekyll-themes]: https://jekyllrb.com/docs/themes/
