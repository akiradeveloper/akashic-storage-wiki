akashic-storage uses **typesafe config** for its configuration.

The configuration is as follows:

```
akashic.storage {
  backend {
  }

  # IP address or hostname to bind.
  ip = localhost

  # port to bind.
  port = 10946

  # akashic-storage uses Basic authentication scheme for the admin APIs.
  # Users need to add Authorization header to access admin APIs:
  # Authorization: Basic base64encode("admin:${admin-passwd}")
  admin-passwd = passwd
}
```