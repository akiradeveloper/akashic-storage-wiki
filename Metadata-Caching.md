akashic-storage stores every metadata files so it causes more than one file reads against the backing filesystem per a GET request. Depending on the backing filesystem type, the extra file reads other than the data file causes non-negligible performance damage. This typically matters when the filesystem is distributed because it may pay for extra communications between the nodes.

This is where metadata caching comes. Because the files managed under akashic-storage are immutable, never overwritten partially, they are **almost**-safely cacheable.

The caching mechanism akashic-storage implements is perfectly safe if the backing filesystem is the local filesystem and only one akashic-storage instance has exclusive access to the backing store.