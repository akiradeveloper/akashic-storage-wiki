To start using akashic-storage in your production environment the best way is to install server daemon and operate the daemon via Linux's traditional sysvinit scripts (e.g. `service akashic-storage start`)

## Initial Installation
To install the daemon, please run

```
$ cd installer
$ make
# make install
```

The following stuffs are installed into your server:

```
/etc/init.d/akashic-storage
/opt/akashic-storage/jar/akashic-storage.jar
/opt/akashic-storage/etc/application.conf
/opt/akashic-storage/etc/logback.xml
/opt/akashic-storage/log
/opt/akashic-storage/run
```

## Update (jar file only)

```
$ cd installer
$ make
# make update
```