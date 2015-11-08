Heroku buildpack: ZBAR
======================

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) for apps requiring ZBAR as a dependency. It is configured to work with the [ruby zbar gem](https://github.com/willglynn/ruby-zbar) but should work with other stacks.

Adding to an existing Ruby App
---------------
1. `heroku config:set ZBAR_LIB=vendor/lib/libzbar.so`
2. `heroku buildpacks:add --index 1 https://github.com/sheck/heroku-buildpack-zbar`

Requirements
------------

1. The `ZBAR_LIB` config variable must be set to `vendor/lib/libzbar.so`. Sharing environment variables between buildpacks is difficult, so it's best to just set it globally.
2. This buildpack must be loaded before the ruby build pack. Running `heroku buildpacks` should return:
````
  === [Your App Name] Buildpack URLs
  1. https://github.com/sheck/heroku-buildpack-zbar
  2. heroku/ruby
````
if it does not, remove the ruby buildpack and re-add it to move it to the bottom.
