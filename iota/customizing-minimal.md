## Customizing Minimal

See https://github.com/pages-themes/minimal

I used `jekyll new test` to see what went into a Gemfile, which is like a package.json file

I copied the Gemfile into daveseah.github.io

I modified it to use github-pages and specified the theme. A Gemfile apparently is just a bunch of files? Not sure

Then according to Gemfile comments, ran `bundle install` followed by `bundle update github-pages`, which because I hadn't run install before didn't do anything new.

I think I can run it now by doing `bundle exec jekyll serve` and navigating to localhost:4000...it shows!

Some errors: 

* `invalid theme folder: _includes`
* `invalid theme folder: _includes`
* `GitHub Metadata: site.name is set in _config.yml, but many plugins and themes expect site.title to be used instead. To avoid potential inconsistency, Jekyll GitHub Metadata will not set site.title to the repository's name.`
* `GitHub Metadata: No GitHub API authentication could be found. Some fields may be missing or have incorrect data.`

The hint on the [_includes error](https://qoolixiloop.github.io/qool-jekyll_step_by_step-loop/jekyll/tutorial/2019/01/22/jekyll-step-by-step-tutorial.html) is that the theme's gemfile doesn't have one.

* `ls $(bundle show jekyll-theme-minimal)`
* `open $(bundle show jekyll-theme-minimal)` and copy everything

remove `theme: jekyll-theme-minimal` from _config.yml
remove `gem "jekyll-theme-minimum"` from Gemfile since we're not longer referring to it

The 'Github Metadata' error always appears on local sites

