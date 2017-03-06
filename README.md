# Some Interesting Gems


## Abstract Type

abstract_type:
[surce](https://github.com/dkubb/abstract_type){:target="_blank"}
[doc](http://www.rubydoc.info/gems/abstract_class/1.0.1){:target="_blank"}

#### Summary

Once included in a class, this class cannot be instantiated, but its descendants can. Also allows hide instance methods and class methods to its descendants.

#### Dependencies

* none

#### How to use

* Add to the destination class with `include AbstractType`, then the target class will raise an error when receive a `new` message.
* Use `abstract method :bar` to make the `bar` method raise an error if it's called from a descendant instance.
* Use `abstract_singleton_method :baz` to make the `baz` method raise an error if it's called from a descendant class.

## Equalizer

equalizer:
[source](https://github.com/dkubb/equalizer){:target="_blank"}
[doc](http://www.rubydoc.info/gems/equalizer/0.0.11){:target="_blank"}

#### Summary

Module to define equality, equivalence and inspection methods in terms of attribute readers.

#### Dependencies

* none

#### How to use

* Just call `include Equalizer.new(:lat, :long)` at the class, and the methods `:==, :eql?, :equal?, :hash` will be available in the class instances. Equality is definied in terms of values of designed attributes (in this case: `:lat, :long`).
* You need to add `attr_reader` and set these attributes before compare (usually at `initialize`).

## Memoizable

memoizable:
[source](https://github.com/dkubb/memoizable){:target="_blank"}
[doc](http://www.rubydoc.info/gems/memoizable/0.4.2){:target="_blank"}

#### Summary

Memoizable makes an optimization that saves the return value of a method so it doesn't need to be re-computed every time that method is called.

#### Dependencies

* thread_safe

#### How to use

* Add `include Memoizable` in the class, and call `memoize :my_method` to make `:my_method` save return value in the first call and use saved value in subsequent calls.
* Be aware that if the instance changes, memoized value could be wrong. Then the best fit for this functionality is a frozen object (immutable).

## Ice Nine

ice_nine:
[source](https://github.com/dkubb/ice_nine){:target="_blank"}
[doc](http://www.rubydoc.info/gems/ice_nine/0.11.2/IceNine/RecursionGuard/ObjectSet){:target="_blank"}

#### Summary

Deep freeze ruby objects


#### Dependencies

* none

#### How to use

* As an utility function:
  * `array  = IceNine.deep_freeze([ 'a', 'b', 'c'  ])`, returns a deep frozen array (it works with several objects), or
  * `object = IceNine.deep_freeze!(Object.new)` that skips deep_freezing of frozen objects.
* As a core extension of object (not required by default):
  * After require `ice_nine` and `ice_nine/core_ext/object`, you can freeze any object with `object.deep_freeze`.


## Adamantium

adamantium
[source](https://github.com/dkubb/adamantium){:target="_blank"}
[doc](http://www.rubydoc.info/gems/adamantium/0.2.0){:target="_blank"}

#### Summary

Create immutable objects with ease. It allows you to make objects immutable in a simple, unobtrusive way.

#### Dependencies

* ice_nine
* memoizable

#### How to use

* It works as a deep immutable object
  * `include Adamantium` in the class, and make its instances immutable
  * It allows `memoize` with aditionals options:
    * `memoize :foo`, memoize `:foo` method response and deep freeze it
    * `memoize :foo, freezer: :noop`, memoize `:foo` method response but do not freeze it
    * `memoize :foo, freezer: :flat`, memoize `:foo` method response and do a standard `freeze` on it (not a deep freeze)
  * In your class a method could call `transform` with a block, that returns a **new instance** with the changes passed to the block.
* It works as a shallow frozen
  * `include Adamantium::Flat` in the class
  * Instance will be frozen, but attributes not.
  * Default memoized behaviour will be `:flat`

## Anima

anima:
[source](https://github.com/mbj/anima){:target="_blank"}
[doc](http://www.rubydoc.info/gems/anima/0.3.0){:target="_blank"}

#### Summary

Simple library to declare read only attributes on value-objects that are initialized via attributes hash.

#### Dependencies

* abstract_type (this is not used)
* adamantium
* equalizer

#### How to use

* In the target class `include Anima.new(:one, :two)`, that makes:
* The initialize method expect a hash with all the keys: `:one, :two`
* You get an `attr_reader` for each key
* Define equality of instances of this class when all attributes are equal
* The instances are immutable, but can call `:with` with new values for some keys, and it returns a new instance with updated values
* The `:to_h` method returns its attributes

## Concord

concord:
[source](https://github.com/mbj/concord){:target="_blank"}
[doc](http://www.rubydoc.info/gems/concord/0.1.5){:target="_blank"}

#### Summary

Mixin to ease compositions in ruby.

#### Dependencies

* adamantium
* equalizer

#### How to use

* In target class `include Concord.new(:foo, :bar)`, and you will get an `initializer` that accepts two positionals parms (foo, bar), protected attribute readers for the each attribute, and equality for target class instances depending on the attributes defined (equalizer). There are a maximum of 3 attributes allowed.
* If you want public attributes instead of the default protected ones, use `include Concord::Public(:foo, :bar)`.

## Procto

procto:
[source](https://github.com/snusnu/procto){:target="_blank"}
[doc](http://www.rubydoc.info/gems/procto/0.0.3){:target="_blank"}

#### Summary

Turns your ruby object into a method object.

#### Dependencies

* none

#### How to use

* When is included with `include Procto.call`
  * The class should have a method `:call`
  * The initializer could receive args, and store in instance variables.
  * You will call the method with `TargetClass.call(args)` and it runs `initialize` with `args`, and then runs `:call`
* When is included with `include Procto.call(:foo)`
  * The class should have a method `:foo`
  * The initializer could receive args, and store in instance variables.
  * You will call the method with `TargetClass.call(args)` and it runs `initializer` with `args`, and then runs `:foo`

## Devtools

devtools:
[source](https://github.com/mbj/devtools){:target="_blank"}
[doc](http://www.rubydoc.info/gems/devtools/0.1.16){:target="_blank"}

#### Summary

Authomatize run of all dev tools with `rake ci`

#### Dependencies

* adamantium
* anima
* concord
* flay
* flog
* mutant
* mutant-rspec
* procto
* rake
* reek
* rspec
* rspec-core
* rspec-its
* rubocop
* simplecov
* yard
* yardstick


#### How to use

* In `spec_helper.rb` add `require 'devtools/spec_helper'`
* You will need a config/ folder with these files:
  * flay.yml
  * flog.yml
  * mutant.yml
  * reek.yml
  * rubocop.yml
  * yardstick.yml
* Is expected to find unit tests under `spec/unit/` and integration tests under `spec/integration/`
* run with `rake ci` or `rake -T` for see all the tasks available
* You will need a Rakefile with at least:


```ruby
require 'bundler'
require 'devtools'
Devtools.init_rake_tasks
```

## Mutant

mutant:
[source](https://github.com/mbj/mutant){:target="_blank"}
[doc](http://www.rubydoc.info/gems/mutant/0.8.12){:target="_blank"}

#### Summary

Mutant is a mutation testing tool for Ruby.

The idea is that if code can be changed and your tests do not notice, then either that code isn't being covered or it does not have a speced side effect.

#### Dependencies

* abstract_type
* adamantium
* anima
* ast
* concord
* diff-lcs
* equalizer
* ice_nine
* memoizable
* morpher
* parallel
* parser
* procto
* regexp_parser
* unparser


#### How to use

* `mutant --use rspec <TestedClassName>` in enough for a single class test
* `mutant -h` shows all the options allowed
* With devtools it becomes easy with `config/mutant.yml` file, you can run `rake metrics:mutant`

