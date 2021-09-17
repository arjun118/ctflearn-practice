[challenge file](https://mega.nz/#!LoABFK5K!0sEKbsU3sBUG8zWxpBfD1bQx_JY_MuYEWQvLrFIqWZ0)

after downloading the file run the strings command.
>strings <file_name>

we have two useful findings
https://mega.nz/#!z8hACJbb!vQB569ptyQjNEoxIwHrUhwWu5WCj1JWmU-OFjf90Prg

**real_unlock_key: Nothing Is As It Seems**

## mega link

we find a zip file named Up for a little challenge.zip

unzip the file,navigate to Did I Forget Again? directory and list all the files.
we will find a hidden file named .Processing.cerb.4 which is indeed a zip file(use file command).

To unzip this file we need a password.Let's try the one we found above  *Nothing Is As It Seems*


>unzip -P 'Nothing Is As It Seems' hid.zip 
```                                      
Archive:  hid.zip
  inflating: skycoder.jpg
```
closely observing the image....

![image](/images/up_for_flag.PNG)
