## tslint-react-perf

Supplemental performance-based rules related to React & JSX for [TSLint](https://github.com/palantir/tslint/). This library is considered a stopgap until these rules are adopted by tslint-react.

### Usage

tslint-react-perf has peer dependencies on `typescript` and `tslint`.

To use these lint rules with the default preset, use configuration inheritance via the `extends` keyword.
Here's a sample configuration where `tslint.json` lives adjacent to your `node_modules` folder:

```js
{
  "extends": ["tslint:latest", "tslint-react", "tslint-react-perf"],
  "rules": {...}
}
```

### Rules

* `jsx-no-bind-props`
  * Augments the tslint-react `jsx-no-bind` rule with spread and ternary expression checks.
  * Rule options: _none_
* `jsx-no-lambda-props`
  * Augments the tslint-react `jsx-no-lambda` rule with spread and ternary expression checks.
  * Rule options: _none_
* `jsx-no-array-literal-props`
  * Creating new array instances inside the `render` call stack works against _pure component rendering_. When doing an shallow equality check between two lambdas, React will always consider them unequal values and force the component to re-render more often than necessary.
  * Rule options: _none_
* `jsx-no-object-literal-props`
  * Creating new object instances inside the `render` call stack works against _pure component rendering_. When doing an shallow equality check between two lambdas, React will always consider them unequal values and force the component to re-render more often than necessary.
  * Rule options: _none_
* `react-pure-components-have-simple-attributes`
  * Components adhering to _pure component rendering_ semantics can be susceptible to excessive rerenderings if their props are complex types. Complex types will be checked by identity, and if these are created dynamically or change at all, they wil result in unnecessary renders.
* `react-component-classes-should-implement-scu`
  * Components extending React.Component re-render on prop changes by default. This may not be desirable. To minimize re-renders, these components should either implement `shouldComponentUpdate()` or extend `React.PureComponent` instead of `React.Component`

### Development

Quick Start (requires Node v6+, yarn v0.22+):

1.  `yarn`
1.  `yarn prepare`
