## Includes
Includes allow you to include other templates into your file.<br>
One thing to note is that you currently can't use variable names with includes.
<br>
***Example of how to use includes***<br>
**File strcuture**
```
________tmplates
    |___base.pug
    |___others
    |   |______ example.pug
```

**others/example.pug**
```pug
include other/example.pug
```

**others/base.pug**
```pug
include other/example.pug
```