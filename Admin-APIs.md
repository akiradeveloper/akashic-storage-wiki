To manage user accounts, you need to talk to the server via HTTP requests

* Add a user: `POST /admin/user`
* Lookup a user: `GET /admin/user/$userId`
* Update a user: `PUT /admin/user/$userId + entity (:: XML)`

Basic authentication scheme is required to add to any API requests.
The admin password is specified in `admin-passwd` (see [Configuration](https://github.com/akiradeveloper/akashic-storage/wiki/Configuration)) and then the header to add is `Authorization: Basic base64encode("admin:#{admin-passwd}")`.
