## Why S3 REST APIs are important

Since the appearance of AWS, it's common to use the on-demand cloud infrastructure especially among web developers. What web developers want to do with storage isn't "create an file handle, then write sequence of data and then close it" but simply "put a file" (atomically). This is why the S3 REST APIs are popular among them web developers.

## Why on-premise S3 storage is important

However, there are cases AWS S3 can't use for reasons like:

* Security: they don't want to put data on cloud. This is a strong reason for building a on-premise S3 storage.
* Running cost: AWS S3 is reasonable for small business but when it's big enough, the running cost becomes huge and the performance isn't optimal. A case is Dropbox begun to leave AWS S3 but build their own on-premise storage system in their own data center.

For these reasons, I think it's quite meaningful to develop a S3 storage for on-premise use. The software should be open source and people should get access to the source code otherwise they can't get enough confidence for the production.

