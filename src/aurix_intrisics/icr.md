# Module `icr`

## \_\_restore

```rust
pub unsafe fn __restore(state: bool)
```

### Description

Restore the Interrupt Enable bit (ICR.IE) to the value in `state`.

Generate RESTORE D[a] (SYS)

## \_\_enable

```rust
pub unsafe fn __enable()
```

### Description

Enable interrupts by setting the Interrupt Enable bit (ICR.IE) in the Interrupt Control Register (ICR) to one.

Generate ENABLE (SYS)

## \_\_disable

```rust
pub unsafe fn __disable() -> bool
```

### Description

Disable interrupts by clearing Interrupt Enable bit (ICR.IE) in the Interrupt Control Register. Returns with
the ICR.IE value prior to clearing.

Generate DISABLE D[a] (SYS)
