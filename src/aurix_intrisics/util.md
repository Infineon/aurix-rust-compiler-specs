# Module `util`

## \_\_rsubs

```rust
pub unsafe fn __rsubs<const IMM9: i16>(a: i32) -> i32
```

### Description

Subtract signed `a` from the value IMM9 and returns the result, with saturation on signed overflow.
The value IMM9 is sign-extended before the operation is performed.

Generate RSUBS D[c], D[a], const9 (RC)s

## \_\_rsubsu

```rust
pub unsafe fn __rsubsu<const IMM9: i16>(a: u32) -> u32
```

### Description

Subtract unsigned `a` from the value IMM9 and returns the result, with saturation on unsigned overflow.
The value IMM9 is sign-extended before the operation is performed.

Generate RSUBS.U D[c], D[a], const9 (RC)s

## \_\_satb

```rust
pub unsafe fn __satb(a: i32) -> i8
```

### Description

If signed `a` is less than -128, then return -128. If signed `a` is greater than 127, return 127. Otherwise, return `a`.

Generate SAT.B D[c], D[a] (RR)

## \_\_satbu

```rust
pub unsafe fn __satbu(a: u32) -> u8
```

### Description

If unsigned `a` is greater than 255, then return 255. Otherwise return `a`.

Generate SAT.BU D[c], D[a] (RR)

## \_\_sath

```rust
pub unsafe fn __sath(a: i32) -> i16
```

### Description

If signed `a` is less than -32,768, then return -32,768. If signed `a` is greater than 32,767,
then 32,767. Otherwise return `a`.

Generate SAT.H D[c], D[a] (RR)

## \_\_sathu

```rust
pub unsafe fn __sathu(a: u32) -> u16
```

### Description

If unsigned `a` is greater than 65,535, then return 65,535. Otherwise return `a`.

Generate SAT.HU D[c], D[a] (RR)

## \_\_bmerge

```rust
pub unsafe fn __bmerge(a: u16, b: u16) -> u32
```

### Description

Take the lower 16-bits of `a` and move them to the odd bit positions of the return value.
The lower 16-bits of `b` are moved to the even bit positions of the return value. The upper 16-bits of `a` and
`b` are not used.

Generate BMERGE D[c], D[a], D[b] (RR)

## \_\_bsplit

```rust
pub unsafe fn __bsplit(a: u32) -> (u16, u16)
```

### Description

Split `a` into a tuple such that all the even bits of `a` are in return_value.0 and all the odd bits of `a`
are in return_value.1.

Generate BSPLIT E[c], D[a] (RR)

## \_\_cls

```rust
pub unsafe fn __cls(a: u32) -> u32
```

### Description

Returns the number of consecutive bits which have the same value as bit 31 `a`, starting with bit 30.
The result is the number of leading sign bits minus one, giving the number of redundant sign bits in `a`.

Generate CLS D[c], D[a] (RR)

## \_\_crc32b

```rust
pub unsafe fn __crc32b(seed: u32, input: u8) -> u32
```

### Description

Calculate the CRC of the 8-bit `input` and return the result. `seed` contains either an initial seed value,
or the cumulative CRC result from a previous sequence of data.

Generate CRC32.B D[c], D[b], D[a] (RR)

## \_\_crc32bw

```rust
pub unsafe fn __crc32bw(seed: u32, input: u32) -> u32
```

### Description

Calculate the CRC of `input` and return the result. `seed` contains either an initial seed value, or the
cumulative CRC result from a previous sequence of data. The four bytes in the `input` are processed in big-endian order.

Generate CRC32B.W D[c], D[b], D[a] (RR)

## \_\_crc32lw

```rust
pub unsafe fn __crc32lw(seed: u32, input: u32) -> u32
```

### Description

Calculate the CRC of `input` and return the result. `seed` contains either an initial seed value, or the
cumulative CRC result from a previous sequence of data. The four bytes in the `input` are processed in little-endian order.

Generate CRC32L.W D[c], D[b], D[a] (RR)

## \_\_crcn

```rust
pub unsafe fn __crcn(
    seed: u16,
    width: u32,
    generator: u32,
    data: u16,
    data_width: u32,
    little_endian: bool,
    invert: bool,
) -> u16
```

### Description

Calculate the CRC value for 1 to 8 bits of input data using a user-defined CRC algorithm with a CRC width from 1 up
to 16 bits. `seed` contains an initial seed value. `data` contains the input data. The result is returned.

The `width` parameter contains the CRC width in the range [1,16].

The processing of the input data depends on the `little_endian` flag. For little-endian bit order, the bit `data`[0]
is processed first. For big-endian bit order, the bit `data`[0] is processed last.

If `invert` is true, a bitwise logical inversion is applied to both the result and seed values. `seed` contains either an initial
seed value, or the cumulative CRC result from a previous sequence of data. The `seed` value should be initialized according to
the chosen CRC algorithm. Note that the `invert` flag must be taken into account when specifying the seed as the inversion is applied
to the initial seed value as well as the final result.

The `generator` parameter encodes the coefficients of the generator polynomial. The coefficient of the most significant
term is omitted as it must be 1 by definition. `generator`[`width`-1:0] contains the remaining coefficients, stored with the
highest term in `generator`[`width`-1] and lowest term in `generator`[0]. E.g., the CRC-8-SAE J1850 polynomial is encoded as 1DH.
All unused bits in the `generator` must be zero.

The `data_width` parameter contains the input data width in the range [1,8].

The `data` parameter contains the input data. Exactly `data_width` bits of input data are processed. The CRC result is returned.
The bits return_value[`width`-1:0] contains the CRC result and all other bits are set to zero. The return can be used as the seed input
for a subsequent CRCN instruction. By chaining CRCN instructions in this way data larger than 8 bits in length can be processed.

WARNING: input parameters are not checked, they are passed as is to the CRCN instruction.

Generate CRCN D[c], D[d], D[a], D[b] (RRR)
