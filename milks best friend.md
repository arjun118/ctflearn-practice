[challenge link](https://mega.nz/file/DC5F2KgR#P8UotyST_6n2iW5BS1yYnum8KnU0-2Amw2nq3UoMq0Y)

extract the contents of the image file using binwalk
>binwalk -e <image_file>

you will find a rar file
>unrar e <rar_filename>

the text file named a read
```
This is not the flag you are looking for
```
we get a new file named  b.jpg

>strings b.jpg | grep flag

flag: **flag{eat_more_oreos}**
