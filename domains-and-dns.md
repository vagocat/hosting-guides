# Domains & DNS records explained

DNS is the phone book of the internet: it turns a name people can remember (`yoursite.com`) into the address a computer needs (an IP like `198.51.100.23`). Here are the records you'll actually use.

## The core records

| Record | What it does | Example |
|--------|--------------|---------|
| **A** | Points a name to an IPv4 address | `yoursite.com → 198.51.100.23` |
| **AAAA** | Points a name to an IPv6 address | `yoursite.com → 2001:db8::1` |
| **CNAME** | Makes one name an alias of another (not allowed on the root domain) | `www → yoursite.com` |
| **MX** | Says which server receives your email (with a priority) | `10 mx1.mailprovider.com` |
| **TXT** | Free-form text — used for SPF, DKIM, domain verification | `v=spf1 ...` |
| **NS** | The authoritative nameservers for your domain | `ns1.vagocat.com` |

## TTL (Time To Live)

TTL is how long resolvers cache a record, in seconds. 

- **Before a migration:** lower it to `300` (5 minutes) a day ahead, so changes take effect fast.
- **When stable:** raise it back to `3600`–`86400` for better performance.

## Common gotchas

- **No CNAME on the root** (`yoursite.com`). Use an A record, or your host's ALIAS/ANAME.
- **Propagation isn't instant** — allow up to a few hours (bounded by the old TTL).
- **One change at a time** when debugging, so you know what fixed it.

---

Hosting your domain with [Vagocat](https://vagocat.com)? You can manage all of these records from your control panel in a couple of clicks.
