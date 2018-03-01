!!Redirection Operators ''>'' and ''>>''

*The redirection operator ''>'' causes a file creation, and if it does exist, the contents are overwritten. 
*The redirection operator ''>>'' add information to the end of file, rather than replacing it.

!!View all the open ports
```
netstat -nlt
```

!!Copying files and directories using scp

```
#from local to remote
scp /path/to/file1 user@remotehost:/remotedir/file1

#from remote to local
scp user@remotehost:/remotedir/file1 /path/to/local/file1

#copy the 'remotedir' directory recursive to the current directory
scp -r user@remotehost:/remotedir .
```

!!Deleting all recursive

```
rm -rf /path/*
```

!!Memoria disponible:

```
free -m
```

!!Disk space and inode usage

```
df -h --total
df -i --total
```

!!Watch a file on real time:

```
#chequear cada 1seg las ultimas 10 lineas del archivo kern.log)
watch -n 1 sudo tail /var/log/kern.log

#va mostrando lo nuevo que se le añade a fichero.log
tail -f fichero.log
```

!!Para compactar/descompactar un archivo en ''.tar.bz2''

```
#Compactar archivo a tar.bz2
tar -c carpeta_a_compactar | bzip2 > carpeta_compactada.tar.bz2

#Descompactar archivo a tar.bz2
tar jvxf archivo_a_descompactar.tar.bz2

#Descompactar un archivo en ''.tar.gz''
tar -zxvf archivo_a_descompactar.tar.gz
```

!!Para ver todas las interfaces de red

```
sudo lshw -class network
sudo update-rc.d -f apache2 remove
```

!!Stop services from starting on boot

```
sudo update-rc.d -f apache2 remove
```

!!Size of all items in a file

```
du -sk -- * | sort -n | perl -pe '@SI=qw(K M G T P); s:^(\d+?)((\d\d\d)*)\s:$1." ".$SI[((length $2)/3)]."\t":e'
```

!!Get all repositories

```
grep -r --include '*.list' '^deb ' /etc/apt/sources.list*
```
