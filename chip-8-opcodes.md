# CHIP-8 - OP Codes

CHIP-8 opcodes are `u16` values made up of 4 nibbles (half-bytes, 4-bit value). There isn't a 4-bit value in Rust. CHIP-8 nibbles are often recombined to form either 8-bit or 12-bit values dependent on context.

Each opcode is made up of two bytes: the _high byte_ and the _low bite_. Each byte is made of two nibbles, the _high nibble_ and the _low nibble_.

| **Variable** | **Bit Length** | **Location**                                    | **Description** |
| ------------ | -------------- | ----------------------------------------------- | --------------- |
| n\*          | 4              | low byte, low nibble                            | Number of bytes |
| x            | 4              | high byte, low nibble                           | CPU register    |
| y            | 4              | low byte, high nibble                           | CPU register    |
| c            | 4              | high byte, high nibble                          | Opcode group    |
| d            | 4              | low byte, low nibble                            | Opcode subgroup |
| kk           | 4              | low byte, both nibble                           | integer         |
| nnn          | 4              | high byte, low nibble and low byte, both nibble | memory address  |

The decoding process involves matching on the high nibble of the first byte and applying one of three strategies.

![method 1]("/images/method-1.png")
![method 2]("/images/method-2.png")
![method 3]("/images/method-3.png")
