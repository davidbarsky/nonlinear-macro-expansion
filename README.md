With two calls to a pathological tt-muncher:

```
time ~/.cargo/bin/rust-analyzer analysis-stats .
[crates/load-cargo/src/lib.rs:338:5] "loading crate graph" = "loading crate graph"
[crates/load-cargo/src/lib.rs:374:22] crate_graph.len() = 12
Database loaded:     1.55s, 0b (metadata 331.15ms, 0b; build 342.53ms, 0b)
  item trees: 1
Item Tree Collection: 5.61ms, 0b
  crates: 1, mods: 1, decls: 1004, bodies: 3, adts: 1001, consts: 0
Item Collection:     2.08s, 0b
Body lowering:       4.85s, 0b
  exprs: 573, ??ty: 254 (44%), ?ty: 0 (0%), !ty: 0
  pats: 11, ??ty: 0 (0%), ?ty: 0 (0%), !ty: 0
Inference:           397.53ms, 0b
MIR lowering:        424.04µs, 0b
Mir failed bodies: 2 (66%)
Data layouts:        4.51ms, 0b
Failed data layouts: 0 (0%)
Const evaluation:    0.00ns, 0b
Failed const evals: 0 (100%)
Total:               7.34s, 0b

________________________________________________________
Executed in    9.11 secs    fish           external
   usr time    7.36 secs    0.09 millis    7.36 secs
   sys time    0.77 secs    1.07 millis    0.77 secs
```

With one:

```
at 04:47:50 PM ❯ time ~/.cargo/bin/rust-analyzer analysis-stats .
[crates/load-cargo/src/lib.rs:338:5] "loading crate graph" = "loading crate graph"
[crates/load-cargo/src/lib.rs:374:22] crate_graph.len() = 12
Database loaded:     1.90s, 0b (metadata 336.76ms, 0b; build 285.98ms, 0b)
  item trees: 1
Item Tree Collection: 5.07ms, 0b
  crates: 1, mods: 1, decls: 1003, bodies: 2, adts: 1001, consts: 0
Item Collection:     2.11s, 0b
Body lowering:       2.43s, 0b
  exprs: 292, ??ty: 127 (43%), ?ty: 0 (0%), !ty: 0
  pats: 7, ??ty: 0 (0%), ?ty: 0 (0%), !ty: 0
Inference:           382.33ms, 0b
MIR lowering:        322.67µs, 0b
Mir failed bodies: 1 (50%)
Data layouts:        4.96ms, 0b
Failed data layouts: 0 (0%)
Const evaluation:    0.00ns, 0b
Failed const evals: 0 (100%)
Total:               4.93s, 0b

________________________________________________________
Executed in    7.01 secs    fish           external
   usr time    5.08 secs   61.00 micros    5.08 secs
   sys time    0.68 secs  611.00 micros    0.68 secs
```

With none:

```
at 04:49:08 PM ❯ time ~/.cargo/bin/rust-analyzer analysis-stats .
[crates/load-cargo/src/lib.rs:338:5] "loading crate graph" = "loading crate graph"
[crates/load-cargo/src/lib.rs:374:22] crate_graph.len() = 12
Database loaded:     1.25s, 0b (metadata 210.82ms, 0b; build 132.64ms, 0b)
  item trees: 1
Item Tree Collection: 4.22ms, 0b
  crates: 1, mods: 1, decls: 1002, bodies: 1, adts: 1001, consts: 0
Item Collection:     1.96s, 0b
Body lowering:       1.40ms, 0b
  exprs: 11, ??ty: 0 (0%), ?ty: 0 (0%), !ty: 0
  pats: 3, ??ty: 0 (0%), ?ty: 0 (0%), !ty: 0
Inference:           336.22ms, 0b
MIR lowering:        210.67µs, 0b
Mir failed bodies: 0 (0%)
Data layouts:        4.23ms, 0b
Failed data layouts: 0 (0%)
Const evaluation:    209.00ns, 0b
Failed const evals: 0 (100%)
Total:               2.30s, 0b

________________________________________________________
Executed in    3.68 secs    fish           external
   usr time    2.56 secs    0.09 millis    2.56 secs
   sys time    0.32 secs    1.59 millis    0.32 secs
```