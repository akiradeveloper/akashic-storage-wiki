While you are able to manage user accounts through raw HTTP requests (Admin APIs), it's bit bothering to make raw HTTP requests by `curl` command or some library. That's where akashic-admin CLI comes in.

The akashic-admin CLI is written in Go and has the following sub commands:

* config - Make a config file under HOME directory
* add - Add a user
* get $userId - Get a user
* (TODO) list - List users
* (TODO) update - Update a user

## How to install

```
$ cd akashic-admin
$ make
# make install
```

Note that Golang compiler is prerequisite and the actual binaries are installed at `/usr/local/bin`. To uninstall, just do `make clean`.