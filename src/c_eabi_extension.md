# C EABI Extension

The RUST language defines 128-bit scalar data types and uses functions returning a pair of scalar values. The EABI describes only the standard C-types up to 64-bit and the standard C-function interface allowing the return of one value.

The handling of the 128-bit types needs an additional entry to describe the size and alignment.
| type | Size in bytes | Alignment | description |
|------|---------------|-----------|-------------|
| i128 | 16 | 16 | signed 128-bit integer |
| u128 | 16 | 16 | unsigned 128-bit integer |
