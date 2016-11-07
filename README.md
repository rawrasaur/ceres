# Ceres #

[![Build Status](https://travis-ci.org/rawrasaur/ceres.svg?branch=master)](https://travis-ci.org/rawrasaur/ceres)

Ceres is a gem that extends the Ruby standard library with some cool new features, but it doesn't monkey patch anything or break anything you already have, so just require what you want or go all in with `require 'ceres'`. The main features are mostly immutable type safe classes, synchronized objects, notification centers, and thread pools.

The main goal is to allow sloppy people like me write good code by catching errors instead of just silently letting them slip.


## Installation ##

If you're using bundler you can just add this line to your application's Gemfile:

```ruby
gem 'ceres'
```

And then execute:

    $ bundle install

Or install it yourself as:

    $ gem install ceres


## Structure ##

If you wanted to define a cookie class, you could do it as follows and then Ceres would verify the types and enums.

```ruby
require 'ceres/structure'

class Cookie < Ceres::Structure
  attribute :name, type: String
  attribute :type, enum: [:chocolate_chip, :almond, :anzac]
  attribute :niceness, type: Fixnum, default: 11
  
  array :ingredients
end

Cookie.new(name: 'Best Cookie', type: :chocolate_chip)
```

The valid options are as follows

 - type: limits value to certain class
 - enum: limits value to certain values
 - default: sets default
 - optional: value can be nil
 - element_type: elements limited to certain class


`array` is just a shorthand for setting type to `Array`.


## Development ##

After checking out the repo, run `bin/setup` to install dependencies. Then, run `rake spec` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).


## License ##

Ceres is released under the MIT license:

www.opensource.org/licenses/MIT


## Contributing ##

Bug reports (and pull requests) are appreciated on GitHub at https://github.com/rawrasaur/ceres, I'm sorry if I'm slow at responding.
