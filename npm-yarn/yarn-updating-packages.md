## Yarn and how it handles version control with dependicies

```
--------
---- parent-package
      |-- child-package
 	|-- package-we-care-about-^v1.0.10
 ---- parent-package
      |-- child-package
 	|-- package-we-care-about-^v2.0.5
```

If we look at the structure of our dependency tree above, you'll notice that we have three levels and the component we're trying to update is `package-we-care-about`.

Ideally when we run `yarn install` we'd like to have atleast version `v2.0.5` or higher in our `node_modules` foler which gets created and used.

However running `yarn install` or `yarn upgrade` will make points in your `yarn.lock` file but what will actually get used is a version no higher than a major version of `1`.

I beleive Yarn does this a safe measure to older packages don't break terribly when accidently upgrading major versions.

So it could be `v1.110.1` but never `2.0.0`.

To get around this you will have to manually go into your package and version bump the package yourself.
