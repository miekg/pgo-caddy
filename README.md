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

Together with the 2 branches of miekg/pgo-website and this config, you should have a working pgo
setup. This does HTTP only setup. The 'caddy1.miek.nl' and 'caddy2.miek.nl' dns names should be put
in /etc/hosts.

~~~ toml
[[services]]
name = "default"
user = "root"
repository = "https://github.com/miekg/pgo-caddy"
import = "caddy/Caddyfile-import"
reload = "localhost:caddy//exec caddy reload --config /etc/caddy/Caddyfile --adapter caddyfile"

[[services]]
name = "caddy1"
user = "miek"
repository = "https://github.com/miekg/pgo-website"
env = [ "SHARE=/tmp", "NETWORK=caddy1" ]
urls = { "http://caddy1.miek.nl" = "caddy1-caddy-1:80" }
networks = [ "reverseproxy" ]

[[services]]
name = "caddy2"
user = "miek"
repository = "https://github.com/miekg/pgo-website"
env = [ "SHARE=/tmp", "NETWORK=caddy2" ]
urls = { "http://caddy2.miek.nl" = "caddy2-caddy-1:80" }
networks = [ "reverseproxy" ]
~~~
