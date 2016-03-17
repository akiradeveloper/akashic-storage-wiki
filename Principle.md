This article explains how akashic-storage works and why it's durable for failures.

When you boot up the akashic-storage server you can see the minimal tree structures under the mountpoint you specified in the configuration. You might wonder what astral is. It's quite a valid question.

```
mountpoint/
├── admin
│   └── db
├── astral
└── tree
```

When in failure, some PUT Object request might leave metadata and data partially. Maybe only metadata are written or data is written but partial (and we can't tell that). In any storage systems, such kind of problem always annoys the developer. To commit atomically, transaction is often used but it's overkill for akashic-storage.

My answer is always making a complete set of files beforehand under **astral** and move it to under **tree** (mv is at least an atomic operation in POSIX compliant filesystem and most of the distributed filesystem is so) and when the object is removed from tree, we always move back the object and into astral. So, astral is where everything born and die. How romantic.

What gives us by doing so is not the transactional write to the storage but that we can trust completeness of the contents under tree. Which allows us to avoid runtime checks if the object is really complete. This makes akashic-storage simple and faster.

