# Module `csfr`

## \_\_mfcr

```rust
pub unsafe fn __mfcr<const REG: u16>() -> u32
```

### Description

Return the contents of the Core Special Function Register (CSFR), selected by the value REG.

Generate MFCR D[c], const16 (RLC)

## \_\_mtcr

```rust
pub unsafe fn __mtcr<const REG: u16>(value: u32)
```

### Description

Move the value in `value` to the Core Special Function Register (CSFR) selected by the value REG.

Generate MTCR const16, D[a] (RLC)

## \_\_mfdcr

```rust
#[cfg(target_feature = "tc18")]
pub unsafe fn __mfdcr<const REG: u16>() -> u64
```

### Description

Return the contents of the Core Special Function Registers (CSFR), selected by the value REG and REG+4.

Generate MFDCR E[c], const16 (RLC)

## \_\_mtdcr

```rust
#[cfg(target_feature = "tc18")]
pub unsafe fn __mtdcr<const REG: u16>(value: u64)
```

### Description

Move the value in `value` to the Core Special Function Registers (CSFR) selected by the value REG and REG+4.

Generate MTDCR const16, E[a] (RLC)
