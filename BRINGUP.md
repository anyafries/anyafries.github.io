# Local bring-up

How to build and preview this site on your machine.

## Run it (day-to-day)

```bash
bundle exec jekyll serve
```

Open **http://localhost:4000/** — `baseurl` is empty, so the site is at the root
(not `/al-folio/`, despite what the upstream al-folio docs say).

- Auto-reload the browser on save: `bundle exec jekyll serve --livereload`
- Stop the server: `Ctrl-C`
- **Editing `_config.yml`? Restart the server** — Jekyll does not hot-reload config.

## Production-style build (optional)

```bash
bundle exec jekyll build      # writes the static site to _site/
```

## One-time setup (fresh machine)

macOS ships Ruby 2.6, which is too old — this project needs Ruby ≥ 3.2 (its
`Gemfile.lock` uses Bundler 4). Install a modern Ruby with rbenv:

```bash
brew install rbenv ruby-build
echo 'eval "$(rbenv init - zsh)"' >> ~/.zshrc && exec zsh
rbenv install 4.0.5
rbenv local 4.0.5             # pins Ruby for this repo (creates .ruby-version)
gem install bundler -v 4.0.6
bundle install
```

Verify with `ruby -v` (should print 4.0.5), then run the serve command above.

Notes:
- conda `(base)` in your PATH is fine; the appended rbenv init line takes
  precedence so `ruby` resolves to rbenv's Ruby, not the system 2.6.
- If `ruby -v` still shows 2.6 after `exec zsh`, your conda init is running
  last — move the rbenv `eval` line to the very end of `~/.zshrc`.
