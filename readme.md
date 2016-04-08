# babel-plugin-throws-helper [![Build Status](https://travis-ci.org/jamestalmage/babel-plugin-throws-helper.svg?branch=master)](https://travis-ci.org/jamestalmage/babel-plugin-throws-helper)

> internal AVA internal plugin for protecting against improper use of `t.throws`

Probably not useful except as an internal plugin for the AVA test runner.

Genesis of the idea: https://github.com/sindresorhus/eslint-plugin-ava/issues/75

## Issue

> I've seen a lot of incorrect use of the throws assertion in other test runner and even done the mistake myself sometimes. Now I'm beginning to see it with AVA too, so would be nice to be preemptive about it.
>
> People don't realize they need to wrap their call in a function, so many end up doing `t.throws(foo())` instead of `t.throws(() => foo());`. It's an easy mistake to make.


The difficulty is that `t.throws(foo())` is allowed if `foo()` returns a promise or a function. There is no good way to differentiate between the two at runtime. So providing a good error message is going to take some AST transform magic.

## The solution

See `example-output.md` for the transformation this performs.

The example output can be generated by calling:

```
$ WRITE_EXAMPLES=1 ava
```

Contributors should not commit new examples. They will be regenerated as part of the release process.

## License

MIT © [James Talmage](http://github.com/jamestalmage)
