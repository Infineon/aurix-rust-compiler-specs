# Module `trap`

## \_\_syscall

```rust
pub unsafe fn __syscall<const TIN: u16>()
```

### Description

Cause a system call trap, using the Trap Identification Number (TIN).

Generate SYSCALL const9 (RC)

## \_\_trapinv

```rust
pub unsafe fn __trapinv() -> !
```

### Description

Trap on Invalid Code

Generate TRAPINV

## \_\_trapsv

```rust
pub unsafe fn __trapsv()
```

### Description

If the PSW sticky overflow status flag (PSW.SV) is set, generate a trap to the vector entry for the sticky overflow trap
handler.

Generate TRAPSV (SYS)

## \_\_trapv

```rust
pub unsafe fn __trapv()
```

### Description

If the PSW overflow status flag (PSW.V) is set, generate a trap to the vector entry for the overflow trap handler.

Generate TRAPV (SYS)
