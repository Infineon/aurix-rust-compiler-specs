# Module `vm`

## \_\_cacheaivm

```rust
#[cfg(target_feature = "tc18")]
pub unsafe fn __cacheaivm(addr: *const u8)
```

### Description

Invalidate virtual machine cache address.

Generate CACHEA.I.VM A[b].

## \_\_cacheawvm

```rust
#[cfg(target_feature = "tc18")]
pub unsafe fn __cacheawvm(addr: *const u8)
```

### Description

Write back virtual machine cache address.

Generate CACHEA.W.VM A[b].

## \_\_cacheawivm

```rust
#[cfg(target_feature = "tc18")]
pub unsafe fn __cacheawivm(addr: *const u8)
```

### Description

Write back and invalidate virtual machine cache address `addr`.

Generate CACHEA.WI.VM A[b].

## \_\_hvcall

```rust
#[cfg(target_feature = "tc18")]
pub unsafe fn __hvcall<const TIN: u16>()
```

### Description

Allow a virtual machine to call the hypervisor.

Generate HVCALL const9 (RC)

## \_\_rfh

```rust
#[cfg(target_feature = "tc18")]
pub unsafe fn __rfh()
```

### Description

Return From Hypervisor

Generate RFH (SYS)
