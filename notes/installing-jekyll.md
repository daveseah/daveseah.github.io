---
---
## Modifying 

Only filed with front matter are processed. Otherwise, they are copied as static files.

```
# the official jekyll instructions are inconsistent with brew, especially its
# call to use sudo and shitty formatting…there are PATHS TO FOLLOW
# and if you follow them as a series of steps you’ll be fucked
# I’m going with the rbenv install and the local install 
# if you fucked it up due to their instructions
# https://stackoverflow.com/questions/31173968/how-do-you-uninstall-rbenv-on-osx

# Installing ruby the right way Mojave
# see which ruby and gem are running before (macOS default versions)
ruby -v
# ruby 2.3.7p456 (2018-03-28 revision 63024)
gem -v
# 2.5.2.3

# see https://github.com/jekyll/jekyll/issues/7274#issuecomment-425069689
brew install rbenv ruby-build
echo ‘if which rbenv > /dev/null; then eval “$(rbenv init -)”; fi’ >> ~/.bash_profile
source ~/.bash_profile 
# or close term, open new term to exec .bash_profile

rbenv install 2.6.3
rbenv global 2.6.3

# see what got installed and confirm the paths changed
which ruby
ruby -v
# ruby 2.6.3p62 (2019-04-16 revision 67580) [x86_64-darwin18]
which gem
gem -v
# errors 
# 3.0.3
# install bundler which seems to fix the errors
gem install bundler
gem -v
# no errors
# 3.0.3

# see if everything looks right in the gem environment
# also shows current $PATH
gem env

# at this point, gem is installed via homebrew so things are good

# install bundler and jekyll versions LOCALLY
gem install --user-install bundler jekyll
gem env # see what the GEM PATHS are pointing to
ruby -v # see which path to add, get first two digits of version for next line
add 
export PATH=$HOME/.gem/ruby/X.X.0/bin:$PATH # replace X.X.0 with version
to .bash_profile
```