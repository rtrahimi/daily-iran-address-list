# Daily Iran Address List

![Updates](https://img.shields.io/badge/updates-daily%20at%2003%3A00%20UTC-0b7285)
![Type](https://img.shields.io/badge/output-ipv4%20txt%20%7C%20sha256%20%7C%20mikrotik-1f6feb)
![Address List](https://img.shields.io/badge/mikrotik-list%3DNO--VPN-2b8a3e)

Reliable Iran IPv4 prefixes for MikroTik workflows.

## Repository Contents

- `iran_ipv4.txt`: Plain IPv4 CIDR prefixes.
- `iran_ipv4.txt.sha256`: SHA-256 checksum for integrity checks.
- `iran_no_vpn.rsc`: MikroTik import file that adds entries to address-list `NO-VPN` with comment `iTNet-IranAddressList`.
- `mikrotik/itnet_addresslist_sync.rsc`: One-shot script that syncs WhatsApp, Telegram, and Iran lists together.

## Raw Download Links

- https://raw.githubusercontent.com/rtrahimi/daily-iran-address-list/main/iran_ipv4.txt
- https://raw.githubusercontent.com/rtrahimi/daily-iran-address-list/main/iran_ipv4.txt.sha256
- https://raw.githubusercontent.com/rtrahimi/daily-iran-address-list/main/iran_no_vpn.rsc
- https://raw.githubusercontent.com/rtrahimi/daily-iran-address-list/main/mikrotik/itnet_addresslist_sync.rsc

## MikroTik Quick Use

### Import Iran list only

```routeros
/tool fetch check-certificate=no url="https://raw.githubusercontent.com/rtrahimi/daily-iran-address-list/main/iran_no_vpn.rsc" dst-path="iran_no_vpn.rsc"
/ip firewall address-list remove [find where comment="iTNet-IranAddressList"]
/import file-name="iran_no_vpn.rsc"
/file remove [find where name="iran_no_vpn.rsc"]
```

### Import all lists with one script

```routeros
/tool fetch check-certificate=no url="https://raw.githubusercontent.com/rtrahimi/daily-iran-address-list/main/mikrotik/itnet_addresslist_sync.rsc" dst-path="itnet_addresslist_sync.rsc"
/import file-name="itnet_addresslist_sync.rsc"
/file remove [find where name="itnet_addresslist_sync.rsc"]
```

## Update Model

- Data generation and push run on a Linux server.
- Schedule: daily at `03:00 UTC`.
- The sync script is static and can be reused any time.
