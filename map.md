# Map

When used in a functional context, Map is not just a way of iterating over a collection. It is a means of taking an input, processing that input and outputting the result. If the collection has a single value within, this allows a value to run through a sequence of transforms. Effectively calling map is saying 'do this to the value and return the result'. 

```
[value].map(x => alpha(x)).map(x => beta(x)).map(x => charlie(x));
```

This is an inversion of a standard function call or sequence of function calls which would need to follow a russian doll pattern:

```
charlie(beta(alpha(value)));
```



