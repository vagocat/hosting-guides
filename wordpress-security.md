# WordPress security checklist

WordPress runs a huge share of the web, which makes it a target. The good news: a handful of basics stop almost every automated attack. Work down this list.

## The essentials

- [ ] **Strong admin password + 2FA** on every admin account.
- [ ] **Avoid the `admin` username** — create a uniquely-named admin and delete `admin`.
- [ ] **Keep core, themes and plugins updated** — most hacks exploit known, already-patched bugs.
- [ ] **Remove what you don't use** — deactivate *and delete* unused plugins/themes.
- [ ] **Daily backups**, stored off the server (so you can always roll back).
- [ ] **Free SSL / HTTPS** on the whole site.

## A step further

- [ ] **Limit login attempts** (plugin or server rule) to block brute force.
- [ ] **Restrict `wp-admin`** by IP if you have a static IP.
- [ ] **Disable file editing** in the dashboard — add to `wp-config.php`:
  ```php
  define('DISALLOW_FILE_EDIT', true);
  ```
- [ ] **Correct file permissions** — `644` for files, `755` for folders.
- [ ] **A security plugin or WAF** (Wordfence, Sucuri, or a Cloudflare WAF).
- [ ] **Test updates on a staging copy** before applying to the live site.

## If you get hacked

1. Take the site offline / into maintenance mode.
2. Restore from a known-good backup.
3. Change **all** passwords (admin, database, FTP, hosting) and rotate keys.
4. Update everything, then find and close the entry point.

---

Hosting with [Vagocat](https://vagocat.com) gives you free SSL, automatic backups and one-click WordPress installs — the checklist above gets a lot shorter.
