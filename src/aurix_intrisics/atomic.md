# Module `atomic`

## \_\_ldmst

```rust
pub unsafe fn __ldmst(addr: *mut u32, value: u32, mask: u32)
```

### Description

Atomic Load-Modify-Store, store under a `mask` of a `value` to the address `addr`.

Generate LDMST A[b], off10, E[a] (BO)
