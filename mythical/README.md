# mythical bug 

## Problem I: `a.out` where are you? (hard)

You received a compiled `a.out` file from your friend.
However, when you try to execute it, you got

```
zsh: no such file or directory: ./a.out
```

You are absolutely sure it is right there with

```
$ ls -lh a.out
-rwxrwxr-x 1 john john 16K Jul 25 04:34 a.out
```

What is going on?

<details>
<summary>Click to Solution</summary>

1. Googling "zsh: no such file or directory" doesn't give you much info
2. Then you starts random Gooling with "a.out not found" or "file not found but it is there"
3. Luckily, when you Google the **complete** error message "zsh: no such file or directory: ./a.out"
4. Goole tell you it is related to "dynamic link" and `ldd` will gives you more info
5. You run `ldd a.out`, it gives you
```
linux-vdso.so.1 (0x00007ffff8bfa000)
libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fa3d484c000)
/lib64/ld-linux-x86-64.so.1 => /lib64/ld-linux-x86-64.so.2 (0x00007fa3d4a85000)
```
6. You notice that there is a strange link trying to link `ld-linux-x86-64.so.1` to `ld-linux-x86-64.so.2`
7. You ask your friend and turns out that this executable is compiled in an old machine with outdated linker

**Addtional Challenge**
Since this executable is crafted by hand, it can actually by repaired through
directly modifying `a.out` with a hex editor.
Can you recover it?
</details>
