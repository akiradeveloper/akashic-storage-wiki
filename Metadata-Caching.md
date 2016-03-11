akashic-storage stores every metadata files so it causes more than one file reads against the backing store per a GET request. Depending on the backing store type, the extra file reads other than the data file causes non-negligible performance damage. This typically matters when the filesystem is distributed because it may pay for extra communications between the nodes.

This is where metadata caching comes. Because the files managed under akashic-storage are immutable, never overwritten partially, they are **almost**-safely cacheable. Caching small metadata on the RAM can effectively eliminate the extra overhead.

The caching mechanism akashic-storage implements is perfectly workable if the backing store is the local filesystem and only one akashic-storage instance has exclusive access to the backing store.

The problem only occurs when multiple akashic-storage instances share the same distributed filesystem and then a client replace the existing resources. Since it uses a pair of (BasicFileAttributes#fileKey, #creationTime) as the lookup keys. Theoretically, there is some possible hole that the read cache metadata is stale.

The key consists of two information - fileKey and creationTime. fileKey is a unique identifier of the file in the filesystem. It's typically inode-number. But the problem is fileKey may be reused depending on the implementation specific. So replacing a file many times may finally give us the same fileKey that was given before, which potentially leads to stale metadata read. This is why I pair the fileKey with the creationTime. With the timestamp, we can enhance the uniqueness of the key.

However, the problem is creationTime is resolution of a second. Therefore, with pairing the two values though, it's not the perfect solution against the case that the user replace the file very frequently and the same fileKey appears within a second.

Considering that this is a use case of insanity, I am confident the solution is mostly-perfect in ordinary 