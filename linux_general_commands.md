## Copying files and directories using scp

```
#from local to remote
scp /path/to/file1 user@remotehost:/remotedir/file1

#from remote to local
scp user@remotehost:/remotedir/file1 /path/to/local/file1

#copy the 'remotedir' directory recursive to the current directory
scp -r user@remotehost:/remotedir .
```

## Ownership and permission:

```
# change owner
chown -R user:group /path

# change owner but no group owner
chown -R user: /path
```

## Deleting all recursive

```
rm -rf /path/*
```

## Redirection Operators ''>'' and ''>>''

* The redirection operator ''>'' causes a file creation, and if it does exist, the contents are overwritten. 
* The redirection operator ''>>'' add information to the end of file, rather than replacing it.

## View all the open ports
```
netstat -nlt
```

## Available Memory:

```
free -m
```

## Disk space and inode usage

```
df -h --total
df -i --total
```

## Watch a file on real time:

```
#va mostrando lo nuevo que se le añade a fichero.log
tail -f fichero.log
```

## Para compactar/descompactar

```
#Compactar archivo a tar.bz2
tar -c carpeta_a_compactar | bzip2 > carpeta_compactada.tar.bz2

#Descompactar archivo a tar.bz2
tar jvxf archivo_a_descompactar.tar.bz2

#Descompactar un archivo en ''.tar.gz''
tar -zxvf archivo_a_descompactar.tar.gz
```

## Para ver todas las interfaces de red

```
sudo lshw -class network
sudo update-rc.d -f apache2 remove
```

## Stop services from starting on boot

```
sudo update-rc.d -f apache2 remove
```

## Size of all items in a file

```
du -sk -- * | sort -n | perl -pe '@SI=qw(K M G T P); s:^(\d+?)((\d\d\d)*)\s:$1." ".$SI[((length $2)/3)]."\t":e'
```

## Get all Ubuntu repositories

```
grep -r --include '*.list' '^deb ' /etc/apt/sources.list*
```

## Compare files and folders

### With find
This command will save in /tmp/file_list_$FOLDER an alphabetically ordered list of all the files inside $FOLDER, complete with the corresponding sub-folders:

```
find $FOLDER -type f | cut -d/ -f2- | sort > /tmp/file_list_$FOLDER
```

### With rsync
The four command line switches r, v, c and n tell ''rsync'' to perform a ''v''erbose, ''r''ecursive, ''c''hecksum-based synchronization of the two directories, but only for show: ''-n'', in fact, displays what rsync would do IF you did let it free to make the second folder a perfect copy of the first one. The advantage of rsync is that can compare local directories with remote ones.

```
rsync -rvnc -delete todo_sync/ todo_orig/
```

### Graphical interface
And graphically you could use ''meld''

## Recover Linux Grub
```
root (hd1,0)
kernel /boot/vmlinuz-3.0.0-20-generic root=/dev/sda1
initrd /boot/initrd-3.0.0-20-generic
boot
```
