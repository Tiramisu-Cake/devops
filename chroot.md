```text
$ sudo chroot less3
$ bash-5.3# ls
  bash: ls: command not found
$ bash-5.3# exit
  exit
``` 

`$ cp /usr/bin/ls less3/usr/bin/`

`$ cp /usr/bin/cp less3/usr/bin/`

```text
$ sudo chroot less3
$ bash-5.3# ls
  ls: error while loading shared libraries: libcap.so.2: cannot open shared object file: No such file or directory
$ bash-5.3# exit
  exit
```

```text
$ ldd /usr/bin/ls
        linux-vdso.so.1 (0x00007f7eaedf9000)
        libcap.so.2 => /usr/lib/libcap.so.2 (0x00007f7eaed9d000)
        libc.so.6 => /usr/lib/libc.so.6 (0x00007f7eaea00000)
        /lib64/ld-linux-x86-64.so.2 => /usr/lib64/ld-linux-x86-64.so.2 (0x00007f7eaedfb000)
```

`$ cp /usr/lib/libcap.so.2 less3/usr/lib/`

```text
$ sudo chroot less3
$ bash-5.3# ls
  lib64  usr
$ bash-5.3# cp
  cp: error while loading shared libraries: libacl.so.1: cannot open shared object file: No such file or directory
$ bash-5.3# exit
  exit
```
```text
$ ldd /usr/bin/cp
        linux-vdso.so.1 (0x00007f1f611aa000)
        libacl.so.1 => /usr/lib/libacl.so.1 (0x00007f1f6115a000)
        libattr.so.1 => /usr/lib/libattr.so.1 (0x00007f1f61152000)
        libc.so.6 => /usr/lib/libc.so.6 (0x00007f1f60e00000)
        /lib64/ld-linux-x86-64.so.2 => /usr/lib64/ld-linux-x86-64.so.2 (0x00007f1f611ac000)
```
`$ cp /usr/lib/libacl.so.1 less3/usr/lib/`

`$ cp /usr/lib/libattr.so.1 less3/usr/lib/`
```text

$ sudo chroot less3
$ bash-5.3# ls
  lib64  usr
$ bash-5.3# cp
cp: missing file operand
Try 'cp --help' for more information.
bash-5.3# 
```
