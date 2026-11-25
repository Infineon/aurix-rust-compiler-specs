# Module `cache`

## \_\_cacheai

```rust
pub unsafe fn __cacheai(addr: *const u8)
```

### Description

Invalidate cache address.

Generate CACHEA.I A[b].

## \_\_cacheaw

```rust
pub unsafe fn __cacheaw(addr: *const u8)
```

### Description

Write back cache address.\

Generate CACHEA.W A[b].

## \_\_cacheawi

```rust
pub unsafe fn __cacheawi(addr: *const u8)
```

### Description

Write back and invalidate cache address.

Generate CACHEA.WI A[b].
