# anytype_ynh

Unofficial YunoHost package for a self-hosted [any-sync](https://github.com/anyproto/any-sync-dockercompose) network, the sync backend for Anytype.

Anytype accounts are created inside the client and are end-to-end encrypted. The server stores and relays encrypted data only; it never sees the private keys.

## Install

From the YunoHost command line:

```bash
sudo yunohost app install https://github.com/taroxzen/anytype_ynh
```

Or in the YunoHost webadmin: **Applications → Install → custom app URL** and paste the repository URL.

The installer clones the official compose stack into `/opt/any-sync`, generates random S3/Garage secrets, writes `.env`, and starts the containers.

## Requirements

- YunoHost 12.1.17 or newer
- Docker with Compose plugin v2
- ~1 GiB RAM available
- TCP 1001-1006 and UDP 1011-1016 reachable from the clients

Enter the **origin IP** when asked for the public host. A Cloudflare-proxied domain will not forward these raw TCP/QUIC ports.

## Client setup

After installation, copy `/opt/any-sync/etc/client.yml` from the server and import it in the Anytype desktop app: **Settings → Network → Self-hosted → Import configuration**.

Create your account in the app and save the recovery phrase. There is no server-side registration.

## Management

```bash
sudo yunohost app upgrade anytype -u https://github.com/taroxzen/anytype_ynh
sudo yunohost backup create --apps anytype
cd /opt/any-sync && sudo docker compose ps
```

## Notes

- This is not an official Anytype or YunoHost package.
- The any-sync compose stack is MIT licensed. The Anytype client has license terms that may restrict commercial use — review them before deploying for an organization.
- The registered URL (`/anytype` by default) is only a panel entry. There is no web interface there; clients connect over TCP/QUIC with `client.yml`.
