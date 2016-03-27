akashic-storage stores every metadata as files so it causes more than one file reads against the backing store per a GET request. Depending on the backing store type, the extra file reads other than the data file causes non-negligible performance damage. This typically matters when the filesystem is distributed because it may pay for extra communications between the cluster nodes.

This is where metadata caching comes. Because the files managed under akashic-storage are immutable, never overwritten partially, they are mostly safely cacheable. Caching small metadata on the RAM can effectively eliminate the extra overhead.

The caching mechanism akashic-storage implements is perfectly workable if the backing store is the local filesystem and only one akashic-storage instance has exclusive access to the backing store.

The problem only occurs when multiple akashic-storage instances share the same distributed filesystem and then a client replace the existing resources (by "PUT Bucket acl" API for example). Since it uses a pair of (cacheKey, creationTime) of FileAttr as the lookup keys. Theoretically, there is some potential hole that the read cache metadata is stale.

The key consists of two information - cacheKey and creationTime. cacheKey is a unique identifier of the file in the filesystem. It's typically inode-number. But the problem is cacheKey may be reused depending on the implementation specific. So replacing a file many times may finally give us the same cacheKey that was seen before, which potentially leads to stale metadata read. This is why I pair the cacheKey with the creationTime. With the timestamp, we can enhance the uniqueness of the key.

However, the problem is creationTime is often resolution of a second. Therefore, with pairing the two values though, it's not the perfect solution against the case that the user replace the resource very frequently and the same cacheKey appears within a second.

Considering that this is only a use case of insanity, I am confident the solution is almost perfect.