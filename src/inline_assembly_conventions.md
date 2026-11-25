# Inline Assembler

`rustc` supports embedding inline assembly in Rust code via the `asm!` and `global_asm!` macros.

This chapter describes the TriCore-specific register names and features.

For more information about inline assembly in Rust, see _The Rust Reference_.

## ABI Clobbers

### Clobbers

Register names can be added to this list to let the compiler know that the assembly code modifies the register somehow.

For TriCore, the following register names are recognized as clobbers:

#### 32-bit data registers

`d0`, `d1`, `d2`, `d3`, `d4`, `d5`, `d6`, `d7`, `d8`, `d9`, `d10`, `d11`, `d12`, `d13`, `d14`, `d15`

#### 32-bit address registers

`a0`, `a1`, `a2`, `a3`, `a4`, `a5`, `a6`, `a7`, `a8`, `a9`, `a10`, `a11`, `a12`, `a13`, `a14`, `a15`

#### 64-bit extended data registers

`e0`, `e2`, `e4`, `e6`, `e8`, `e10`, `e12`, `e14`

#### 64-bit extended address registers

`p0`, `p2`, `p4`, `p6`, `p8`, `p10`, `p12`, `p14`

## Register Classes

Input and output operands can specify an explicit register class from which the register allocator can select a register.

### Register Classes Supported for TriCore

| Register Class | Description                    |
| -------------- | ------------------------------ |
| `reg32`        | 32-bit data registers          |
| `reg_ptr`      | 32-bit address registers       |
| `reg64`        | 64-bit extended data registers |

Source: Register classes supported for TriCore.

### Example

```rust
let x1: i32 = 3;
let x2: i32 = 3;
let y: i64;

asm!(
    "mov {}, {}, {}",
    out(reg64) y,
    in(reg32) x1,
    in(reg32) x2
);
```

Example adapted from the User Guide.

## Assembly Template Modifiers

### `A`

This modifier is only valid on extended data/address registers and prints the extended register name, for example `e2`.

It is only supported for compatibility with existing sources and can be omitted.

### `L`

This modifier is only valid on extended data/address registers and prints the lower 32-bit register name, for example `d2` for extended data register `e2`. 【1-8d93b6】

### `H`

This modifier is only valid on extended data/address registers and prints the upper 32-bit register name, for example `d3` for extended data register `e2`. 【1-8d93b6】

### Example

```rust
let x: i64 = 3;
let y: i32;

asm!(
    "mov {}, {:H}",
    out(reg32) y,
    in(reg64) x
);
```

Example adapted from the User Guide.
