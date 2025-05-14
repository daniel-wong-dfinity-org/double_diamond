The following command succeeds:

```
cargo build
```

This surprises me, because the `a` library crate directly or indirectly (via `b`
and `c`) depends on THREE different versions of the `base64` crate
(specifically, `=0.1.0`, `=0.11.0`, and `=0.22.1`).

I guess what this means is that as long as you do not try to pass an object of
type `T` that is defined in all three versions from one version of the library
to another, then you are ok?? Well, even if there is a way to make this work, it
could be quite confusing, because the compiler might say something like "T is
required, but T was supplied".
