# ES 2016 - Sets

Sets are similar to Arrays, but ensure the uniqueness of the items they contain.
Adding the same item twice has no effect. 

## Weak Set

Weak sets only allow objects to be added and don't allow values to be read from
them. However it does have a `has` method that returns true if the object passed
is included in the set.
