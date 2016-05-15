The easiest way to try out akashic-storage is to use [Vagrant](https://www.vagrantup.com) virtual machine. It will install everything you need from server daemon to admin-web and set up working akashic-storage service.

**1. First step**

Before launching your Vagrant environment, you must install [VirtualBox 5.x](https://www.virtualbox.org/wiki/Downloads) as [Vagrant](https://www.vagrantup.com/downloads.html). All of these software packages provide easy-to-use visual installers for all popular operating systems.

**2. Boot up Vagrant**

Once you finish installing Vagrant, you can now boot up your Vagrant VM.

```
$ cd vagrant-quick-start
$ vagrant up
```

Now you can access akashic-storage at `http://localhost:10946` and admin-web at `http://localhost:10947`.