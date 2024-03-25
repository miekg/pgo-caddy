# pgo-caddy

Caddy configuration for [pgo](github.com/miekg/pgo).

pgo config:

~~~ toml
[[services]]
name = "default"
user = "root"
repository = "https://github.com/miekg/pgo-caddy"
import = "caddy/Caddyfile-import"
reload = "localhost:caddy//exec caddy reload --config /etc/caddy/Caddyfile --adapter caddyfile"
~~~
