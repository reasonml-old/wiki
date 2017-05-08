

Thanks for interest in contributions.

Note currently our philosphy is to make release build as easy as possible, while dev build is fairly complex at this time.

## Set up dev dependencies

- Having [https://opam.ocaml.org/](opam) installed

    opam switch 4.02.3+buckle-master # use our OCaml compiler
    opam install camlp4 cppo  <1>

   Both `Camlp4` and `cppo` are used to generate OCaml code for pre-processing. 
   Switch to our compiler makes your life easier (avoid confusion with diferent compiler versions)
- Having [https://nodejs.org/](NodeJS) installed
- Having GNU Make installed
- OS: Mac/Linux (Note BuckleScript works well on Windows, but the dev mode is not tested)


All source code are in `jscomp` directory, below assume that you are working in `jscomp` directory.


## components of the compiler

`bs-platform` is composed of several components, the core compiler, the bundled ocaml stdlib,  shipped js bindings, test cases and some internal tools.

### internal tools

- bspack

  bspack is heavily used in `bs-platform`, it is a tool to pack all ocaml 
  source code  into a single file, so that in release mode, there is not any dev dependency anymore.

  It is very stable and heavily tested, in most cases, contributors don't need change its behavior.

  Below are examples of how it is used:

  ```make
  bin/whole_compiler.ml:./bin/bspack.exe
	$< -U BS_DEBUG -bs-MD -prelude-str 'module Config = Config_whole_compiler' -bs-exclude-I config -o $@ -bs-main Js_main -I ../ocaml/utils/ -I ../ocaml/parsing/ -I ../ocaml/typing/ -I ../ocaml/bytecomp/ -I ../ocaml/driver/ -I stubs -I ext -I syntax -I depends -I common -I core
  ```

  `bspack` is bootstrapped by itself, so it is only a single file
  to build `bspack.exe`, run 
  
  ```sh
  make -C bin bspack.exe
  ```
## Dev-Build the compiler binaries
`bspack` makes release build much easier, it is pretty slow during development since it does not do separate compilation. For dev build, we build each component and link them together.

Please refer `./build.sh` for more details

## Release-build the compiler binaries

All changes in compiler much be snapshot using `bspack.exe`, so  that in release build, all binaries are just one ocaml file.

```sh
make force-snapshotml
```
This target will snapshot your changes into such huge files like `bin/whole_compiler.ml`
```sh
make -C bin all
```