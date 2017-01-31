This is a repository of questions & answers related to BuckleScript (but don't really belong in the BS docs) and BuckleTypes. As people ask more questions we'll group the frequently asked ones here. **Please submit yours by filing an issue**!

### What's BuckleScript's async story?
On the native OCaml side, we have [lwt](http://ocsigen.org/lwt/) and [Async](https://ocaml.janestreet.com/ocaml-core/111.03.00/doc/async/#Std). We don't use them in the immediate future. BS would instead bind to JS promises, with some syntactic sugar in the future (maybe in conjunction with Reason!). In the long run, we'd like to implement a spec-compliant promises implementation in OCaml/Reason proper, so that the compiler optimizations could kick in.
