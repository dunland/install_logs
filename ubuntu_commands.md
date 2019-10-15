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

## most basic commands

moving folders: `mv from/path to/path`
rename a folder: `mv /home/user/oldname /home/user/newname`

`history` shows terminal command history

## symlinks
create symlink: `sudo ln -s /path/to/file/file-to-link /destination/folder/`  
show symlink origin: `readlink -f symlinkname`


## Text File Handling

`touch ubuntu_commands.md` creates text file
`gedit ubuntu_commands.md` opens text file for changes

