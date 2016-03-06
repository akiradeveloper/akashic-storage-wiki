To start using akashic-storage in your production environment the best way is to install server daemon and operate the daemon via Linux's traditional sysvinit scripts (e.g. `service akashic-storage start`)

To install the daemon, please run

```
$ cd installer
$ sh compiler-jar.sh
# sh install.sh
```

The following stuffs are installed into your server:

```
/etc/init.d/akashic-storage
/opt/akashic-storage/jar/akashic-storage.jar
/opt/akashic-storage/etc/conf
```

You can update the configuration of the server by modifying `/opt/akashic-storage/etc/conf`. If you want to set mountpoint and ip address from the default values the file should be like:


```
akashic.storage {
  mountpoint = /mnt/nfs/akashic-storage
  ip = 192.168.10.23
}
```