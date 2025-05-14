The following command succeeds:

```
cargo build
```

This surprises me, because the `a` library crate indirectly (via `b` and `c`)
depends on DIFFERENT versions of the SAME library (specifically, they depend on
versions `=0.11.0`, `=0.1.0` of the `base64` crate).

I guess what this means is that as long as you do not try to pass an object of
type `T` that is defined in in one version of a library to the another version
of the same library, then you are ok?? Well, even if there is a way to
indirectly depend on different versions of the same library work, it could be
quite confusing, because the compiler might say something like "T is required,
but T was supplied". And unless all the fields of `T` are public (or something
like this), then, there would be no way to convert from one version of `T` to
another, and you would have no way to fix that error.
