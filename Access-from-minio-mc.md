Because akashic-storage supports AWS S3 APIs it's accessible via any tools/libraries that supports the protocol. But I especially recommend to use [minio/mc](https://github.com/minio/mc) if you access the storage from command line. The design is sophisticated so you can access remote and local storages transparently, debugging mode leaves us useful information when in trouble and moreover, maintained by nice guys.

To configure mc, please run

```
$ mc config host add alias http://$hostname:$port $accessKey $secretKey S3v2
```

Read the documentation in [minio/mc](https://github.com/minio/mc) for more detail.