# BPK1 file structure

BPK1 is a file structure used in almost all game files, and also the letters that you send to your friends. They can optionally be compressed using either LZSS v10 or LZSS v11.

A BPK1 file consists of a header (a "table of contents" if you will) and data blocks. Each data block has a name, indicating what it contains. Names can repeat, in which case the order usually matters.

Integer values are stored as little-endian.

| Offset | Size     | Description                    |
| ------ | -------- | ------------------------------ |
| 0x0    | 0x40     | [BPK1 Header](#bpk1-header)    |
| 0x40   | N * 0x14 | [Block Header](#block-header)s |
|        |          | Block data                     |

## BPK1 Header

| Offset | Size | Description                           |
| ------ | ---- | ------------------------------------- |
| 0x0    | 0x4  | Header magic (BPK1)                   |
| 0x4    | 0x4  | Number of blocks                      |
| 0x8    | 0x4  | Maximum block name length (usually 7) |
| 0xC    | 0x4  | Structure length                      |
| 0x10   | 0x4  | Header length                         |
| 0x14   | 0x2C | Padding                               |

## Block Header

| Offset | Size | Description                              |
| ------ | ---- | ---------------------------------------- |
| 0x0    | 0x4  | Block data offset                        |
| 0x4    | 0x4  | Block size                               |
| 0x8    | 0x4  | [Checksum](#checksum) of block data      |
| 0x10   | 0x8  | Block name, filled with NULLs if shorter |

### Checksum

The checksum of each block is calculated as a custom CRC-32 checksum of the block's data: 
   - Polynomial: 4C11DB7
   - Initial value: 4C11DB7
   - Output XOR: 0

Sample use with the Rust `crc` library can be seen [here](https://github.com/SwapdoodleRevival/libdoodle/blob/906dfad46ffb6177634ea1faebf30b68320c8ee7/src/bpk1/mod.rs#L23).

# BPK1 Blocks

- [SHEET1](./sheet1.md)
- [COMMON1](./common1.md)

# Credits

Most of the information on this page has been taken from [3dbrew.org](https://www.3dbrew.org/wiki/Swapdoodle).