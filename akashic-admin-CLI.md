While you are able to manage user accounts through raw HTTP requests (Admin APIs), it's bit bothering to make raw HTTP requests by `curl` command or some library. That's where akashic-admin CLI comes in.

The akashic-admin CLI is written in Go and has the following sub commands:

* add
* remove
* update
* setup-mc-config (add a user and set up the mc config below the home directory)

## How to install

```
$ cd akashic-admin
$ make
# PREFIX=/usr/local make install
```

Note that Golang compiler is prerequisite and the actual binaries are installed at `PREFIX`/bin.