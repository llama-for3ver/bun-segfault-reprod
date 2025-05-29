# bun-segfault-reprod
Steps to reprod:

Install `my-dep`:
`bun i` (to install from the tarball, not ./my-dep/)

`bun .` will print that it is unpatched.

Now run `bun patch my-dep`
Go into node_modules/my-dep and do whatever
Then run `bun patch --commit 'node_modules/my-dep'`
It then crashes:

```
bun patch v1.2.15 (df017990)
============================================================
Bun v1.2.15 (df017990) macOS Silicon
macOS v15.1.1
CPU: neon fp aes crc32 atomics
Args: "bun" "patch" "--commit" "node_modules/my-dep"
Features: text_lockfile
Elapsed: 3ms | User: 2ms | Sys: 4ms
RSS: 8.88MB | Peak: 8.88MB | Commit: 1.07GB | Faults: 36

panic(main thread): Segmentation fault at address 0x0
oh no: Bun has crashed. This indicates a bug in Bun, not your code.

To send a redacted crash report to Bun's team,
please file a GitHub issue using the link below:

...

[1]    7171 trace trap  bun patch --commit 'node_modules/my-dep'
```
