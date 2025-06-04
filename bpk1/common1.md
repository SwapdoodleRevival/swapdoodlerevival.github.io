# COMMON1

The COMMON1 block contains data about a Letter.

| Offset | Size | Description                                       |
| ------ | ---- | ------------------------------------------------- |
| 0x0    | 0x8  | Letter ID                                         |
| 0x8    | 0x8  | ID of the Letter this Letter is replying to       |
| 0x10   | 0x8  | [Date](#date-format) this note was written.       |
| 0x18   | 0x4  | Principal ID (PID) of the sender                  |
| 0x1C   | ...  | ?                                                 |
| 0x28   | 0x18 | Sender's name as a UTF-16 string, NULL terminated |

## Date format

| Offset | Size | Description                          |
| ------ | ---- | ------------------------------------ |
| 0x0    | 0x1  | Years since 2000                     |
| 0x1    | 0x1  | Month (1 = January, 2 = February...) |
| 0x2    | 0x1  | Day (1 = 1st, ...)                   |
| 0x3    | 0x1  | Hour                                 |
| 0x4    | 0x1  | Minute                               |
| 0x5    | 0x1  | Second                               |
| 0x6    | 0x2  | Zeroed out                           |