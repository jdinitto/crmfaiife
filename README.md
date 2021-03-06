# Calling Returned Methods From An IIFE
This is more for personal reference, but I was fascinated (annoyed) by immediately invoked function expressions (IIFE) that returned consumable methods. These methods would end up returning `undefined` when called, and they were specifically manipulating the DOM.

I found the method calls that did work either:
1. accessed the DOM from within the IIFE itself, or
2. called the method from another function, outside the IIFE and outside the onload callback, or
3. The returned object properties are functions that return one of the private function expressions.

The rest of the method calls returned as `undefined`. Calling the method the first way makes sense, since it's being called as though it were a normal function. The second way works probably because of hoisting: the `zank` function holds the value of the returned object.

THe third way is preferable (to me), since it works both onload and on a post-load event, is self-contained because it doesn't require a separate outside function like `zank()`, and is more reusable outside this specific implementation as it doesn't depend on specific DOM elements like number 1.

I added a new method that better accomplishes what I wanted, called `ponk`. It's pretty simple, as it returns the function expression inside the IIFE. It writes to the DOM at the `window.onload` event, and on the button press. Huzzah! [This post by Ben Alman](http://benalman.com/news/2010/11/immediately-invoked-function-expression/) on IIFEs really cleared things up for me.

[Check it out in action here](https://jdinitto.github.io/crmfaiife)

# To Do
- [x] Research and find a better explanation.
