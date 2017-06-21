# The BuckleTypes FAQ (Few Answered Questions)

This is a repository of questions & answers related to BuckleScript (but don't really belong in the BS docs) and BuckleTypes. As people ask more questions we'll group the frequently asked ones here. **Please submit yours by filing an issue**!

### What's BuckleScript's async story?
First, if you're not interfacing with any library that uses promises, you can simply use callbacks. Everyone gets them and they're performant.

If you need to bind to a JS library that uses promises, or communicate with such library, you can use BS's [bindings to promises](http://bucklescript.github.io/bucklescript/api/Js.Promise.html). There's also potential to have some syntactic sugar in the future. In the long run, we'd like to implement a spec-compliant promises implementation in OCaml/Reason proper, so that the compiler optimizations could kick in.

For a more idiomatic OCaml solution: on the native OCaml side, we have [lwt](http://ocsigen.org/lwt/) and [Async](https://ocaml.janestreet.com/ocaml-core/111.03.00/doc/async/#Std). We don't use them in web right now, but we might in the future.

### What's the (unit) test story?
Some of OCaml's language features (not just types) might be able to defer the need for unit testing until later. In the meantime, for compilation to JS, we're working on [Jest bindings](https://github.com/BuckleTypes/bs-jest). We'll look into using Jest for native too, if Jest is written using Reason in the future (no concrete plan yet). [OUnit](http://ounit.forge.ocamlcore.org) is a good, small native OCaml testing library right now.

### How can I contribute to the ecosystem?
One way is to look at the [BuckleTypes index](https://github.com/BuckleTypes/index), see if you find an unfinished binding or library (which is most of them) and contribute to that. Or if you can think of something you'd like to exist that isn't listed, just start coding and submit your project to the index for others to discover!

There's also plenty of documentation that needs writing. For most all of the bindings and libraries in the index. Even if there isn't any documentation yet add doc comments (and an interface file if there isn't even that) to the code. For some really high-impact documentation work, you could help improve the BuckleScript manual or API reference. Have a look at the [documentation contribution guide](http://bucklescript.github.io/bucklescript/Manual.html#_contributing_to_the_documentation).

Or if you feel really adventurous, you could try your hand at contributing to the BuckleScript compiler or one of the Reason tools. See the respective contrbution guide for [BuckleScript](http://bucklescript.github.io/bucklescript/Manual.html#_contributions) or [Reason](https://github.com/facebook/reason#contributing).

You could also write blog posts, do [conference talks](https://github.com/vramana/awesome-reasonml#reason-talks), make YouTube videos or just chat peoples ears off about how great this thing is!

#### Contribution to the core compiler

See  [here](./contrib-compiler.md)