# Tips

## Protecting from inexistent properties, when testing property values

Prefer the [`in` operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/in) — which will return `true` for a property with a value of `false` or `undefined`…

```javascript
"isPending" in userResource && userResource.isPending === false
```

… instead of the [`dot` property accessor](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Property_Accessors) — which would short-circuit the evaluation, when a property was defined, but holds either an undefined or a false value, because both are _falsy_ boolean values:

```javascript
userResource.isPending && userResource.isPending === false
```
