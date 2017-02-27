## Immediately-Invoked Function Expression

Also known as IIFE for short. It executes immediately after it’s created.


This pattern is often used when trying to avoid polluting the global namespace, because all the variables used inside the IIFE (like in any other normal function) are not visible outside its scope.

```
(function() {
  ...
})
```
