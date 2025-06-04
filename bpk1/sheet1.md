# SHEET1

The SHEET1 block contains the data for the actual doodle. Each SHEET1 block contains "strokes" that are used to paint the doodle. For each stroke, a point is drawn onto the canvas, optionally drawing a line if the previous stroke instructed so.

## Header

| Offset | Size      | Description          |
| ------ | --------- | -------------------- |
| 0x00   | 4 bytes   | Always 98 3A 00 00 ? |
| 0x04   | 4 bytes   | Number of strokes    |
|        |           | Padding              |
| 0x40   | N*4 bytes | [Stroke](#stroke)s   |

## Stroke

Each stroke is 4 bytes long with the following format:

| Offset | Size   | Description                                                           |
| ------ | ------ | --------------------------------------------------------------------- |
| 0x0    | 4 bits | Lower 4 bits of Y position                                            |
|        | 4 bits | ?                                                                     |
| 0x1    | 4 bits | Higher 4 bits of X position                                           |
|        | 4 bits | Higher 4 bits of Y position                                           |
| 0x2    | 1 bit  | ?                                                                     |
|        | 1 bit  | If set, the next stroke will be a line from this position to the next |
|        | 1 bit  | If set, draw in the 3D layer                                          |
|        | 1 bit  | ?                                                                     |
|        | 4 bits | Lower 4 bits of X position                                            |
| 0x3    | 4 bits | ?                                                                     |
|        | 1 bit  | If set, draw using the bold pen                                       |
|        | 3 bits | Pen slot in the COLSLT1 block                                         |