# Move a website with zero downtime

Switching hosts sounds scary, but with the right order your visitors never notice. The trick: **set everything up on the new host and test it *before* you point your domain at it.**

## Step by step

1. **Lower your DNS TTL** to `300` a day before — so the final switch propagates in minutes.
2. **Provision the new host** — match the PHP/database versions, create the databases and users, enable SSL.
3. **Copy everything** — files + database to the new server. Configure the app (`wp-config.php`, env variables, etc.).
4. **Test before switching** — edit your computer's `hosts` file to preview the site on the new server using the real domain. Check pages, forms, email and cron jobs.
5. **Final sync** — just before cutover, sync any files/database rows that changed (`rsync` for files, a fresh DB export for data).
6. **Cut over** — update the A record to the new IP. Watch the logs; confirm SSL and email still work.
7. **Keep the old host** for a few days as a safety net before cancelling.

## Easy to miss

- **Hardcoded URLs** in the database — run a search-replace (use WP-CLI for WordPress and serialized data).
- **Cron jobs** — recreate them on the new host.
- **Email** — if mail was on the old host, move mailboxes too, or MX will still point at the old server.

---

Moving to [Vagocat](https://vagocat.com)? **Free migration is included** — tell us where your site lives now and we'll handle it with zero downtime.
