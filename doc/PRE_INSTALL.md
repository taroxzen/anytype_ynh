Requires Docker with the Compose plugin v2 and about 1 GiB of available RAM. The stack publishes TCP 1001-1006 and UDP 1011-1016; make sure those ports are reachable from your clients.

You will be asked for the public IP or hostname that Anytype clients should connect to. A Cloudflare-proxied hostname will not work for these raw TCP/QUIC ports — use the origin IP.
