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

equalizer:
[source](https://github.com/dkubb/equalizer)
[doc](http://www.rubydoc.info/gems/equalizer/0.0.11)

#### Summary

Module to define equality, equivalence and inspection methods in terms of attribute readers.

#### Dependencies

* none

#### How to use

* Just call `include Equalizer.new(:lat, :long)` at the class, and the methods `:==, :eql?, :equal?, :hash` will be available in the class instances. Equality is definied in terms of values of designed attributes (in this case: `:lat, :long`).
* You need to add `attr_reader` and set these attributes before compare (usually at `initialize`).

## Memoizable

memoizable:
[source](https://github.com/dkubb/memoizable)
[doc](http://www.rubydoc.info/gems/memoizable/0.4.2)

#### Summary

Memoizable makes an optimization that saves the return value of a method so it doesn't need to be re-computed every time that method is called.

#### Dependencies

* thread_safe

#### How to use

* Add `include Memoizable` in the class, and call `memoize :my_method` to make `:my_method` save return value in the first call and use saved value in subsequent calls.
* Be aware that if the instance changes, memoized value could be wrong. Then the best fit for this functionality is a frozen object (immutable).

## Ice Nine

ice_nine:
[source](https://github.com/dkubb/ice_nine)
[doc](http://www.rubydoc.info/gems/ice_nine/0.11.2/IceNine/RecursionGuard/ObjectSet)

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
[source](https://github.com/dkubb/adamantium)
[doc](http://www.rubydoc.info/gems/adamantium/0.2.0)

#### Summary

Create immutable objects with ease. It allows you to make objects immutable in a simple, unobtrusive way.

#### Dependencies

* ice_nine
* memoizable

#### How to use

*

## Anima

anima:
[source](https://github.com/mbj/anima)
[doc]()

#### Summary



#### Dependencies

*

#### How to use

*

## Concord

concord:
[source](https://github.com/mbj/concord)
[doc]()

#### Summary



#### Dependencies

*

#### How to use

*

## Procto

procto:
[source](https://github.com/snusnu/procto)
[doc]()

#### Summary



#### Dependencies

*

#### How to use

*

## Devtools

devtools:
[source]()
[doc]()

#### Summary



#### Dependencies

*

#### How to use

*

## Mutation

mutation:
[source]()
[doc]()

#### Summary



#### Dependencies

*

#### How to use

*

