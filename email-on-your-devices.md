# Set up your business email on iPhone, Android and Outlook

You have a mailbox like `info@yourbusiness.com`. Here's how to read and send it from your phone and your computer, so it works just like Gmail.

## The settings you need

Write these down — every app asks for the same things. Replace `yourbusiness.com` with your own domain.

| Setting | Value |
|---------|-------|
| **Email address** | your full address, e.g. `info@yourbusiness.com` |
| **Username** | your full address again (not just `info`) |
| **Password** | your mailbox password |
| **Incoming server (IMAP)** | `mail.yourbusiness.com` · port `993` · SSL/TLS |
| **Outgoing server (SMTP)** | `mail.yourbusiness.com` · port `465` · SSL/TLS (or `587` · STARTTLS) |
| **Outgoing server needs a login?** | Yes — same username and password |

> **IMAP or POP3?** Choose **IMAP**. It keeps your phone, laptop and webmail in sync. POP3 (port `995`) downloads mail to one device and is only useful for very old setups.

## iPhone and iPad

1. Open **Settings → Mail → Accounts → Add Account → Other → Add Mail Account**.
2. Enter your name, full email address, password and a description. Tap **Next**.
3. Choose **IMAP**, then fill in the incoming and outgoing servers from the table above.
4. Tap **Save**. Mail starts arriving within a minute.

## Android (Gmail app)

1. Open **Gmail → your profile picture → Add another account → Other**.
2. Type your full email address, then choose **Personal (IMAP)**.
3. Enter your password, then the incoming and outgoing servers from the table.
4. Keep **"Require sign-in"** on for the outgoing server and finish.

## Outlook (Windows and Mac)

1. Go to **File → Add Account** (on Mac: **Outlook → Settings → Accounts → +**).
2. Enter your email address, open **Advanced options** and tick **Let me set up my account manually**.
3. Choose **IMAP** and enter the servers and ports from the table.
4. Enter your password and click **Connect**.

## Something not working?

- **"Cannot verify server identity"** — your domain isn't pointing to your host yet, so the security certificate for `mail.yourbusiness.com` hasn't been issued. Wait until DNS has updated, then try again.
- **Can receive but not send** — check the outgoing port (`465` with SSL/TLS) and that the outgoing server uses your username and password.
- **Wrong password** — the username must be the *full* email address.
- **Just need it quickly?** Use **webmail** in any browser: `https://webmail.yourbusiness.com`.

---

Professional email from [Vagocat](https://vagocat.com/professional-email) includes webmail, spam filtering and these exact settings — and our team will happily set up your devices with you.
