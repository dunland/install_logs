# Ubuntu Commands

## Core / Architecture Info

### Print certain system information.

``` bash 
dav@dav-lx:~$ uname -a
Linux dav-lx 4.15.0-55-lowlatency #60-Ubuntu SMP PREEMPT Tue Jul 2 19:11:22 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
dav@dav-lx:~$ uname -m
x86_64
```

`top` -- task manager

## files and folders

moving folders: `mv from/path to/path`  
rename a folder: `mv /home/user/oldname /home/user/newname`  

changing folder ownership: `sudo chown -R $USER ~/.blabla` (Make the current user own everything inside the folder (and the folder itself))  

list permission of folder: `ls -l`

example for weird, password-protected folder "zoom":  
``` bash
dav@dav-ubu:~/2019/zoom$ ls -l
total 20
drwx------ 12 root root 4096 Okt 22 00:41  4CH
-rw-------  1 dav  dav     0 Okt 21 23:33  4CH000I.wav
drwxrwxr-x  2 dav  dav  4096 Okt 21 23:34  FOLDER06
drwx------  6 root root 4096 Okt 22 00:41  MTR
drwxr-xr-x 12 root root 4096 Okt 22 00:42  STEREO
drwxr-xr-x  2 root root 4096 Okt 22 00:42 'System Volume Information'
```



## terminal

`history` shows terminal command history

## symlinks
create symlink: `sudo ln -s /path/to/file/file-to-link /destination/folder/`  
show symlink origin: `readlink -f symlinkname`


## Text File Handling

`touch ubuntu_commands.md` creates text file
`gedit ubuntu_commands.md` opens text file for changes

