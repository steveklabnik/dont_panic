Don't panic!()
==============

Ensure that code can't panic at compile time.

Example
-------

This code will compile and (not) run just fine:

```rust
let should_panic = false;
if should_panic {
    dont_panic!("This will never execute.");
}
```

However, this code will cause linking error:

```rust
let should_panic = true;
if should_panic {
    dont_panic!("This will never execute.");
}
```

Caveats
-------

* This works only when appropriate opt_level is specified - it may require release build.
* The error message is weird link error. You don't get line number, etc.
* There may be situations in which you know that the code is unreachable but compiler can't prove it.
