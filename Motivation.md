**Why: S3 REST APIs**

Since the appearance of Amazon Web Service (AWS), it's common to use the on-demand cloud infrastructure especially among web developers. What web developers want to do with storage isn't "create an file handle, then write sequence of data and then close it" but simply "put a file" (atomically). This is why the S3 REST APIs are popular among them web developers.

**Why: On-premise S3 storage**

However, there are cases AWS S3 can't be useful for reasons like:

* Security: They don't want to put data on cloud for security reason. This is a strong reason for building an on-premise S3 storage.
* Running cost: AWS S3 is reasonable for small business but when it's extended, the running cost becomes huge and the performance isn't optimal. A case is Dropbox began to leave AWS S3 and builds their own on-premise storage system in their data center.

For these two reasons, I think it's quite meaningful to develop a S3 storage for on-premise use. The software should be open-source and people should get access to the source code because otherwise they can't get enough confidence for the production use. My goal is to make this software the de-facto-standard S3 software with users world-wide.

**Why: Need to develop from scratch**

There are softwares available at this time to build on-premise S3 storage but none of them can't satisfy my requirements. The requirements are:

1. The S3 API service layer and the data storage backend should be separate. Different users want to use different storage backend because of the learning cost, their know-hows and performance requirements.  
2. It should be applicable to distributed filesystem in a robust way. Otherwise the storage isn't scalable in both size and performance.  
3. It should be written in statically typed language. Otherwise it's hard to maintain as open-source project and it's preferable to written in functional programming language which can achieve higher clarity of codes.
4. Of course, it should be open-source.

Here is the comparison:

| Name | Satisfies |
|:--|:--|
| Akashic Storage | ALL |
| Riak CS | 2, 4 |
| Minio/minio | 3, 4 |
| Cloudian | 2 |

**Why: Scala/Akka-HTTP**

I choose to use Scala language to implement akashic-storage because I believe writing in softwares in (even not purely) functional way is the most effective way to extinguish bugs from the software. The functional code is often even readable because side-effects are hidden under the codes.

Akka-HTTP is chosen because although it's still experimental it's the next de-facto HTTP framework provided by Lightbend (former Typesafe) instead of Play. The codebase is inherited from Spray, a known light-weight HTTP framework so Akka-HTTP has a potential to be greatly performant.

**Why: The Name**

I named this software akashic-storage for the following reasons:

* akashic records is a imaginary storage that stores all memories of the past and the future without any data-loss. akashic-storage is named hoping higher scalability and durability.
* My name **Ak**ira. Some string match.