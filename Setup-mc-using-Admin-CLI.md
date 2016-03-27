This is a case study of creating a user account and setup mc for the user.

Please run a akashic-storage server and install admin-cli, mc beforehand.

## In the server (admin should do this)

**Configure akashic-admin**

```
$ akashic-admin-config
```

**Creating an account**

```
$ akashic-admin-add 
ujdi6HyF4A8jiGWW43JcQuU5ppX1YtrxZEEvmxRDOfNrnYnJL1q1zSKAIzGbLdEw
```

**Getting an account info**

```
$ akashic-admin-get ujdi6HyF4A8jiGWW43JcQuU5ppX1YtrxZEEvmxRDOfNrnYnJL1q1zSKAIzGbLdEw
<User>
  <Id>ujdi6HyF4A8jiGWW43JcQuU5ppX1YtrxZEEvmxRDOfNrnYnJL1q1zSKAIzGbLdEw</Id>
  <AccessKey>EKW3WJKHBOWW1WUPOYAP</AccessKey>
  <SecretKey>NG5B57DPkqQqyjBkTo6Ja4m2pCRCoFEOUj5UXjyR</SecretKey>
  <Name>noname</Name>
  <Email>noname@noname.org</Email>
  <DisplayName>noname</DisplayName>
</User>
```

And then tell the user the accessKey and secretKey in this XML. (Don't give the whole XML)

## At the client side

```
$ mc config host add alias http://$hostname:$port EKW3WJKHBOWW1WUPOYAP NG5B57DPkqQqyjBkTo6Ja4m2pCRCoFEOUj5UXjyR S3v2
```