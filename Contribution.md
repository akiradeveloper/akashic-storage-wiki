Your contribution is welcome.

If you find a bug or find a nice refactoring please open a new Github issue and let us discuss it.

## How to efficiently kill a bug using s3-tests

The quickest way to find a bug is picking up a test in error or failure result from s3-tests. You can access to the latest s3-tests's **Raw Log** on Travis CI.

For example you find a failed test `FAIL: s3tests.functional.test_s3.test_put_object_ifnonmatch_overwrite_existed_failed`. Then you can reproduce the single test by running akashic-storage server in debugging mode by the following steps:

**1. Run RunServer**

Run a `akashic.storage.app.RunServer` application in debugging mode on your local machine. To kill the bug more efficiently, you'd better run the application on the IntelliJ IDE because it gives you a graphical debugging.  

**2. Run the test in a Vagrant VM toward the running server**

```
$ cd vagrant-s3-tests
$ vagrant up
$ vagrant ssh
```

and then

```
$ ./run.sh s3tests.functional.test_s3.test_put_object_ifnonmatch_overwrite_existed_failed
```

The trick is the s3-tests process in the VM accesses to the default gateway in the in-VM network. The connection then routes to the localhost of the local machine. Because `RunServer` application launches the server bound on localhost, the connection from the in-VM process eventually reaches the running server.