# How to Make a Jump Server

* Get a server with fixed IP and ipv6 support; make sure the http/s port, i.e. 80, 443, are available.
* Install `socat`.
* Execute `./start_proxy` by `sudo`; may add the script to `/etc/rc.local`.
* Re-config the DNS A record.
* Test it.

### Best practice
* The DNS A record is a CNAME.
* `supervisord` is recommended. If doing so, see `proxy.conf`.
* The script only proxys traffic over https; it is necessary to redirect traffic from http to https locally,
which is handled by `Apache` or `Nginx`. See the `index.html`.
