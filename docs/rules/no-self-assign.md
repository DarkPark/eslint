# Disallow Self Assignment (no-self-assign)

Self assignments have no effect, so probably those are an error due to incomplete refactoring.
Those indicate that what you should do is still remaining.

```js
foo = foo;
[bar, baz] = [bar, qiz];
```

## Rule Details

This rule is aimed at eliminating self assignments.

The following patterns are considered problems:

```js
/*eslint no-self-assign: 2*/

foo = foo;

[a, b] = [a, b];

[a, ...b] = [x, ...b];

({a, b} = {a, x});
```

The following patterns are considered not problems:

```js
/*eslint no-self-assign: 2*/

foo = bar;
[a, b] = [b, a];

// This pattern is warned by the `no-use-before-define` rule.
let foo = foo;

// The default values have an effect.
[foo = 1] = [foo];
```

## When Not To Use It

If you don't want to notify about self assignments, then it's safe to disable this rule.
