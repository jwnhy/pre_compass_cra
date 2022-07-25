# makefile

## Problem I: `makefile` separator (easy)

Suppose you are new to `make`. You just write an small
`helloworld` program and try to compile it using `make`.

However, when you run `make`, the following error pops up.

```
makefile:2: *** missing separator.  Stop.
```

<details>
<summary>Click to Solution</summary>

1. Googling the error message gives you [this](https://www.google.com.hk/search?q=makefile+missing+separator)
2. Click into one [entry](https://stackoverflow.com/questions/16931770/makefile4-missing-separator-stop)
3. Read it and you know it is due to tab/space
4. Fix it by type `tab` instead of `space` in the makefile

> Some editor may automatically expand `tab` to `space` this can be found by 
> Google `tab space expand <your editor name>`
</details>

## Problem II: This shouldn't work! (medium)

After fixing the above error, you decide to study the concept of *target*
in the `make`. Suddenly, you notice there are something odd with your target
`he1lo`. It is wrong as there is a `1` instead of a `l`.

However, when you try to run it with

```
make hello
```

It still works. How is that possible? Does it means `make` doesn't distinguish
`1` and `l`?

<details>
<summary>Click to Solution</summary>

1. As there are no information available, you decide to Google ["make debug"](https://www.google.com.hk/search?q=make+debug)
2. Clicking into one entry, you learn that `make -d` will gives you more information
3. After trying executing `make hello -d`, `make` prints out a bunch of information
4. Inside [`make_debug_info`](./makefile_debug_info), you notice there is a thing called `implicit rules`
5. Gooling "implicit rules make", gives you a list of [them](https://www.gnu.org/software/make/manual/html_node/Catalogue-of-Rules.html#Catalogue-of-Rules)
6. You learn that these rules can be disabled through `make -r`, after executing that, `make` gives the expected error

```
$ make -r hello
make: *** No rule to make target 'hello'.  Stop.
```
</details>
