The challenge file is a png image file. [chall_file](/images/cut3_c4t.png)

# binwalk

> binwalk  cut3_c4t.png
```
DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 640 x 448, 8-bit/color RGBA, non-interlaced
41            0x29            Zlib compressed data, compressed
167499        0x28E4B         RAR archive data, version 5.x
```
extract the rar file
>binwalk -e cut3_c4t.png

unrar the 28E4B.rar.purrr_2.mp3,y0u_4r3_cl0s3.rar will be inflated

# exiftool

I ran exiftool on the audio file
```
ExifTool Version Number         : 12.30
File Name                       : purrr_2.mp3
Directory                       : .
File Size                       : 81 KiB
File Modification Date/Time     : 2020:03:23 07:54:08-05:00
File Access Date/Time           : 2021:09:17 13:26:26-05:00
File Inode Change Date/Time     : 2021:09:17 13:26:09-05:00
File Permissions                : -rw-r--r--
File Type                       : MP3
File Type Extension             : mp3
MIME Type                       : audio/mpeg
MPEG Audio Version              : 1
Audio Layer                     : 3
Sample Rate                     : 44100
Channel Mode                    : Joint Stereo
MS Stereo                       : On
Intensity Stereo                : Off
Copyright Flag                  : False
Original Media                  : True
Emphasis                        : None
VBR Frames                      : 193
VBR Bytes                       : 78490
VBR Scale                       : 80
Encoder                         : LAME3.99r
Lame VBR Quality                : 2
Lame Quality                    : 0
Lame Method                     : VBR (new/mtrh)
Lame Low Pass Filter            : 18.5 kHz
Lame Bitrate                    : 32 kbps
Lame Stereo Mode                : Joint Stereo
ID3 Size                        : 4151
Artist                          : is a password here?
Audio Bitrate                   : 125 kbps
Duration                        : 5.04 s (approx)
```
*is a password here?* -- this reveals that we may find a password here,but for what?

---

the file command on the other rar file 
y0u_4r3_cl0s3.rar gave

```
y0u_4r3_cl0s3.rar: data
```
the rar file may be corrupted.I opened this file in a hex editor and changed the first three bytes 52 61 72 which are the byte values for a legitimate rar file and saved the file as original.rar

now running a file command shows
```
orginial.rar: RAR archive data, v5
```
if we try to extract the file contents using unrar command it asks for a password.

# audacity
I opened the .mp3 file we extracted using audacity and enabled spectrogram view

![passwd](/images/naughty_cat_audacity.PNG)
password: **sp3ctrum_1s_y0ur_fr13nd**

>unrar e original.rar

supply the above passowrd and read the f1n4lly.txt

```
         __/| 
            \o.O|
       _____(___)______ 
      |       U        |________    __
      |ZjByM241MWNzX21h|        |__|  |_________
      |________________|NXQzcg==|::|  |        /
      |                \._______|::|__|       <
      |                         \::/  \._______\
      |	
      |	                                      
```
>echo ZjByM241MWNzX21hNXQzcg== | base64 -d

flag: **f0r3n51cs_ma5t3r**