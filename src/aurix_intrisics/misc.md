# Module `misc`

## \_\_nop

```rust
pub unsafe fn __nop()
```

### Description

Generate NOP (SR)

## \_\_debug

```rust
pub unsafe fn __debug()
```

### Description

If the Debug mode is enabled (DBGSR.DE == 1), cause a Debug Event; otherwise execute a NOP.

Generate DEBUG (SR)

## \_\_wait

```rust
pub unsafe fn __wait()
```

### Description

Generate WAIT (SYS)
