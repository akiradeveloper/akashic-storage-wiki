By using Admin-CLI it's easy to manage user accounts but administrator still needs to make an account for a request and send him back the user account information. Can we automate this? Yes, we have Admin-Web.

Admin-Web is written in Sinatra and Ruby, and it's a small web application backed by Admin-CLI. Therefore you need to setup Admin-CLI booting up the web app.

### Installation

```
$ gem install bundler
$ cd admin-web
$ bundle install
```

### Start up

```
$ sh run-daemon.sh
```

