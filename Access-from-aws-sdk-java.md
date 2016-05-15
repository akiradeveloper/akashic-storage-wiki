akashic-storage supports [AWS Signature Version 2](http://docs.aws.amazon.com/AmazonS3/latest/dev/S3_Authentication2.html) as the signature process.

You can access the server by either authenticated or unauthenticated (or anonymous) requests.

**Installation**

Visit https://github.com/aws/aws-sdk-java. Use 1.0.97 or higher.


**As an authenticated user**

```java
val conf = new ClientConfiguration
conf.setSignerOverride("S3SignerType") // force to use v2 signature

val cli = new AmazonS3Client(new BasicAWSCredentials(YOUR_ACCESS_KEY, YOUR_SECRET_KEY), conf)
cli.setEndpoint(s"http://SERVER_IP:SERVER_PORT")
cli.setS3ClientOptions(new S3ClientOptions().withPathStyleAccess(true))
```

`withPathStyleAccess(true)` is required because akashic-storage supports "path style" rather than "virtual-hosted style" method (see http://docs.aws.amazon.com/AmazonS3/latest/dev/VirtualHosting.html)

**As an unauthenticated user**

To access as an anonymous user you can use `AnonymousAWSCredentials` instead.

```java
val conf = new ClientConfiguration
val cli = new AmazonS3Client(new AnonymousAWSCredentials(), anonConf)
cli.setEndpoint(s"http://${server.address}")
cli.setS3ClientOptions(new S3ClientOptions().withPathStyleAccess(true))
```