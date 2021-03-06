# README

car: A collection of aliases for common tasks on OCaml projects using ocamlbuild.
(cons was taken!)

Provides shortcuts for common tasks involving OCaml projects, e.g.:
- installing a project as a library
- writing the same list of dependencies to .merlin, _tags, and META
- running _test.ml files

It's intended that you copy this script to your project's directory and
modify it however you see fit. It's called mk because it's easy to type
"./mk" with one hand.

**I will add more documentation soon!**

You're expected to have a directory structure like this:

    project/
      car
      car.toml
      src/
        main.ml
        some_module.ml
        some_module_test.ml
        ...

To create an initial `car.toml` file you can run `./car init`.
You can also install `car` to somewhere on `$PATH` and do `car` instead of
`./car`, although then you won't be able to make customizations per-project.

## Building a toplevel

If you want to build a toplevel using `car top`, running `car topgen` will
splice support code in the following files (paths relative to the root of the
project): 

In `.ocamlinit`:

    #thread
    #directory "src/_build"

In `src/project_top.ml` (replace `project` with the name of your project):

    let () = UTop_main.main ()

`project_top.ml` file is ignored when building your project as a library.

After running `car topgen`, you can run `car top` to build your own custom
toplevel. You can run it with `./project.top` (where `project` is your
project's name).
