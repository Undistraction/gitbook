# The DOM

See: https://developer.mozilla.org/en-US/docs/Web/API/CSS\_Object\_Model/Determining\_the\_dimensions\_of\_elements

## Dimensions

Element dimensions can be accessed through a number of properties. The following hold true _if the element is block-level._

* **offset\[Width/Height\]** is dimension + padding + borders + scrollbar. Dimension is the visible portion in the event of scroll.
* **client\[Width/Height\] **is dimension + padding but not borders or scrollbar. Dimension is the visible portion in the event of scroll.
* **scroll\[Width/Height\] **is dimension + padding. Dimension is total dimension regardless of scrolled amount.

## Layout Thrashing

[List of methods that cause page invalidation](http://ricostacruz.com/cheatsheets/layout-thrashing.html)

Browsers do their best to avoid unnecessary redraws by batching changes that will require a redraw, however certain actions cause an immediate refresh. If we trigger lots of these actions we prevent the browser from optimising the redraws efficiently and this can cause a degradation in performance.

Whenever we read a value that is dependent on an up-to-date layout, the browser has no option but to perform a full page layout which is computationally expensive.



