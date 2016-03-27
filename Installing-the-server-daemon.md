To start using akashic-storage in your production environment the best way is to install server daemon and operate the daemon via Linux's traditional sysvinit scripts (e.g. `service akashic-storage start`)

## Install
To install the daemon, please run

```
$ cd installer
$ make
# make install
```

The following stuffs are installed into your server:

```
/etc/init.d/akashic-storage
/var/run/akashic-storage
/var/log/akashic-storage
/opt/akashic-storage/jar/akashic-storage.jar
/opt/akashic-storage/etc/application.conf
/opt/akashic-storage/etc/logback.xml
```

## Configuration

You can update the configuration of the server by modifying `/opt/akashic-storage/etc/application.conf`. If you want to set mountpoint and ip address from the default values the file should be like:


```
akashic.storage {
  backend {
    type = akashic.storage.backend.Local
    mountpoint = /mnt/akashic-storage
  }
  ip = 192.168.10.23
}
```

and then start the daemon

## Startup

```
$ service akashic-storage start
```

## Update (jar file only)

```
$ cd installer
$ make
# make update
```