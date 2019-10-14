
Using TypeScript 3.7.0-beta.

## Description of problem ##

Running `tsc -b` with repository as-is results in error:

```
TypeError: Cannot read property 'parent' of undefined
    at getOuterTypeParameters (/usr/local/lib/node_modules/typescript/lib/tsc.js:32741:29)
    at getOuterTypeParametersOfClassOrInterface (/usr/local/lib/node_modules/typescript/lib/tsc.js:32792:20)
    at getDeclaredTypeOfClassOrInterface (/usr/local/lib/node_modules/typescript/lib/tsc.js:33026:43)
    at createAnonymousTypeNode (/usr/local/lib/node_modules/typescript/lib/tsc.js:29901:59)
    at typeToTypeNodeHelper (/usr/local/lib/node_modules/typescript/lib/tsc.js:29850:28)
    at /usr/local/lib/node_modules/typescript/lib/tsc.js:29642:106
    at withContext (/usr/local/lib/node_modules/typescript/lib/tsc.js:29686:37)
    at Object.typeToTypeNode (/usr/local/lib/node_modules/typescript/lib/tsc.js:29642:28)
    at typeToString (/usr/local/lib/node_modules/typescript/lib/tsc.js:29609:40)
    at resolveCallExpression (/usr/local/lib/node_modules/typescript/lib/tsc.js:46104:105)
```

NOTE that simply removing the `@constructor` JSDoc annotation from
`src/Dependency.js:7` resolves the problem. `@constructor` IS in fact incorrect,
but it is really difficult to track down what's causing the situation when it
occurs.

This seems to compile fine under 3.6.4.
