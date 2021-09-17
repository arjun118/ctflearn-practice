Challenge reads
```
Dear Santa,

Hey! There are so many toys that I want, but I just don't have the money. I don't care which toy I get as long as it's one or the other, but not both!

```
This sounds something like 'XOR'.

Extracted files are 1.png,3.png.

# binwalk
I ran binwalk on these files

1.png

![1.png](/images/1.png)
```
DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 1280 x 720, 8-bit/color RGBA, non-interlaced
54            0x36            Zlib compressed data, default compression
442           0x1BA           Zlib compressed data, default compression
```
3.png

![3.png](/images/3.png)
```
DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 1200 x 875, 8-bit/color RGBA, non-interlaced
78            0x4E            Zlib compressed data, default compression
52406         0xCCB6          PNG image, 1280 x 720, 8-bit/color RGBA, non-interlaced
52447         0xCCDF          Zlib compressed data, compressed
```

# foremost
I used foremost to extract the other png file that's hidden in 3.png.
>foremost 3.png

as the chall description suggests xor,I used gmic to xor 1.png and the extracted png from 3.png(named 2.png for convinience)

>gmic 1.png 2.png -blend xor -o result.png

after mirrioring the result.png you will see the flag

![result.png](/images/result.png)

flag: **CTFlearn{Santa_1s_C0ming}**


