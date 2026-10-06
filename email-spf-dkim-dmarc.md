# Email that lands: SPF, DKIM & DMARC

If your email goes to spam — or gets rejected — it's almost always because these three records aren't set up. Together they prove your mail is really from you.

## 1. SPF — who is allowed to send

A single TXT record on your domain listing the servers allowed to send mail for you.

```
v=spf1 a mx include:_spf.yourprovider.com ~all
```

- `include:` pulls in your mail provider's own servers.
- `~all` = *soft fail* (mark, don't reject) — use this while setting up.
- Move to `-all` (*hard fail*) once you're confident.

> Keep it to **one** SPF record, and don't exceed 10 `include`/lookups.

## 2. DKIM — a tamper-proof signature

Your mail server signs each message with a private key; the matching public key lives in DNS as a TXT record:

```
mail._domainkey.yoursite.com   v=DKIM1; k=rsa; p=YOUR_PUBLIC_KEY
```

Most hosts (Vagocat included) generate the key and publish the record for you when you add a mail domain.

## 3. DMARC — what to do with failures

Tells receivers how to treat mail that fails SPF/DKIM, and where to send reports. **Start in monitor mode:**

```
_dmarc.yoursite.com   TXT   "v=DMARC1; p=none; rua=mailto:dmarc@yoursite.com"
```

Watch the reports for a couple of weeks, then tighten:

`p=none` → `p=quarantine` → `p=reject`

## Check your work

Tools like **MXToolbox** and **Mail-Tester.com** will tell you instantly whether all three are valid.

---

Email hosting with [Vagocat](https://vagocat.com) sets up SPF & DKIM automatically — you just add DMARC.
