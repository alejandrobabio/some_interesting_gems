# Some Interesting Gems

Document about some gems that include:

* Summary
* Dependencies
* How to use

## Abstract Type

abstract_type:
[surce](https://github.com/dkubb/abstract_type)
[doc](http://www.rubydoc.info/gems/abstract_class/1.0.1)

#### Summary

Once included in a class, this class cannot be instantiated, but its descendants can. Also allows hide instance methods and class methods to its descendants.

#### Dependencies

* none

#### How to use

* Add to the destination class with `include AbstractType`, then the target class will raise an error when receive a `new` message.
* Use `abstract method :bar` to make the `bar` method raise an error if it's called from a descendant instance.
* Use `abstract_singleton_method :baz` to make the `baz` method raise an error if it's called from a descendant class.

## Equalizer

[equalizer](https://github.com/dkubb/equalizer)

## Memoizable

[memoizable](https://github.com/dkubb/memoizable)

## Ice Nine

[ice_nine](https://github.com/dkubb/ice_nine)

## Adamantium

[adamantium](https://github.com/dkubb/adamantium)

## Anima

[anima](https://github.com/mbj/anima)

## Concord

[concord](https://github.com/mbj/concord)

## Procto

[procto](https://github.com/snusnu/procto)

## Devtools

## Mutation
