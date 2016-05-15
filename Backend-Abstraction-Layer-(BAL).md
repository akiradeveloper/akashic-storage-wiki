akashic-storage can serve S3 APIs on top of any storage backend. The `BAL` trait gives you the abstraction to implement the adapter to the backend.

```scala
trait BAL {
  def getRoot: Node
  def isDirectory(n: Node): Boolean
  def moveNode(fromDir: Node, fromName: String, toDir: Node, toName: String)
  def removeNode(dir: Node, name: String)
  def makeDirectory(dir: Node, name: String): Unit
  def lookup(dir: Node, name: String): Option[Node]
  def listDirectory(n: Node): Iterable[(String, Node)]
  def createFile(dir: Node, name: String, data: InputStream): Unit
  def getFileInputStream(n: Node): InputStream
```

The trait defines the minimum set of operations that akachic-storage core requires. It's far simpler than POSIX filesystem APIs so it's possible to realize to work with backends like:

* Pseudo filesystems
* Key-Value stores
* Distributed filesystems
* Other object storages (it can be akashic-storage itself!)

S3 APIs is so complicated if you need to implement from scratch. So if you are developing some distributed filesystem and then have a need to provide S3 APIs, you can use akashic-storage and both you and me will be happy :)