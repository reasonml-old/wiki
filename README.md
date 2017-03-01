This is a repository of questions & answers related to BuckleScript (but don't really belong in the BS docs) and BuckleTypes. As people ask more questions we'll group the frequently asked ones here. **Please submit yours by filing an issue**!

### What's BuckleScript's async story?
First, if you're not interfacing with any library that uses promises, you can simply use callbacks. Everyone gets them and they're performant.

If you need to bind to a JS library that uses promises, or communicate with such library, you can use BS's [bindings to promises](https://github.com/bloomberg/bucklescript-addons/tree/master/bindings/bs-promise). There's also potential to have some syntactic sugar in the future. In the long run, we'd like to implement a spec-compliant promises implementation in OCaml/Reason proper, so that the compiler optimizations could kick in.

For a more idiomatic OCaml solution: on the native OCaml side, we have [lwt](http://ocsigen.org/lwt/) and [Async](https://ocaml.janestreet.com/ocaml-core/111.03.00/doc/async/#Std). We don't use them in web right now, but we might in the future.

### What's the (unit) test story?
Some of OCaml's language features (not just types) might be able to defer the need for unit testing until later. In the meantime, for compilation to JS, we're working on [Jest bindings](https://github.com/BuckleTypes/bs-jest). We'll look into using Jest for native too, if Jest is written using Reason in the future (no concrete plan yet). [OUnit](http://ounit.forge.ocamlcore.org) is a good, small native OCaml testing library right now.
