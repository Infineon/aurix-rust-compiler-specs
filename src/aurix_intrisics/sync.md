# Module `sync`

## \_\_isync

```rust
pub unsafe fn __isync()
```

### Description

Synchronize Instructions.

Generate ISYNC (SYS)

## \_\_dsync

```rust
pub unsafe fn __dsync()
```

### Description

Synchronize Data.

Generate DSYNC (SYS)

## \_\_lsync

```rust
#[cfg(target_feature = "tc18")]
pub unsafe fn __lsync()
```

### Description

Synchronize Local Data

Generate LSYNC (SYS)
