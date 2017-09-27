# Pure Functions

A pure function is one that doesn't change its own inputs. **Given the same input, it will always return the same output. **There are no side-effects.

* This includes a reliance on external data that wasn't passed in to the function, or access of external apis, for example writing to console or disk. 
* This also includes mutation of objects that are passed by reference. Instead of mutating the original object, a new object can be created based on the original with any changes included.
* They are not the same as idempotent functions because idempotent functions can cause side effects _as long as the side-effect is the same every time_.



