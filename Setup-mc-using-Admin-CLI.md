TBD

This is a case study of creating a user account and setup mc for the user.

Please run a akashic-storage server and install admin-cli, mc beforehand.

## In the server (admin should do this)

**Configure akashic-admin**

```
$ akashic-admin-config
```

**Creating an account**

```
$ akashic-admin-add 
```

**Getting an account info**

```
$ akashic-admin-get 
```

## At the client side

```
$ mc config host add alias http://$hostname:$port $accessKey $secretKey S3v2
```