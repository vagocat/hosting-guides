# Your first 10 minutes on a new VPS

You just got a fresh Linux VPS with an IP address and a root password. Before you install anything, spend ten minutes making it safe. These steps are for **Ubuntu 24.04 / 22.04** and **Debian 12 / 13** (AlmaLinux notes at the end).

## 1. Log in

From a terminal (macOS, Linux, or Windows PowerShell):

```bash
ssh root@203.0.113.10
```

Type `yes` the first time, then your root password.

## 2. Update everything

```bash
apt update && apt upgrade -y
```

Fresh images are often a few weeks old. This installs the latest security fixes.

## 3. Create your own user

Working as `root` all day is risky — one typo can break the server.

```bash
adduser alex
usermod -aG sudo alex
```

From now on, log in as `alex` and use `sudo` when you need admin rights.

## 4. Use an SSH key instead of a password

On **your own computer** (not the server):

```bash
ssh-keygen -t ed25519
ssh-copy-id alex@203.0.113.10
```

Test that `ssh alex@203.0.113.10` works **without** asking for the server password. Only then, on the server, turn off password logins:

```bash
sudo sed -i 's/^#\?PasswordAuthentication .*/PasswordAuthentication no/; s/^#\?PermitRootLogin .*/PermitRootLogin no/' /etc/ssh/sshd_config
grep -r PasswordAuthentication /etc/ssh/sshd_config.d/   # cloud images may switch it back on here
sudo systemctl restart ssh
```

If the `grep` shows `PasswordAuthentication yes` in a file under `sshd_config.d/`, change it to `no` in that file too.

> Keep your current session open while you test a new login in a second window. If something is wrong, you can still fix it.

## 5. Turn on the firewall

```bash
sudo apt install -y ufw
sudo ufw allow OpenSSH
sudo ufw allow 80,443/tcp   # only if this will be a web server
sudo ufw enable
```

## 6. Install security updates automatically

```bash
sudo apt install -y unattended-upgrades
sudo dpkg-reconfigure --priority=low unattended-upgrades
```

## 7. Set the hostname and time zone

```bash
sudo hostnamectl set-hostname server1.yourbusiness.com
sudo timedatectl set-timezone Europe/Madrid
```

## AlmaLinux

Use `dnf upgrade -y` instead of `apt`, the `wheel` group instead of `sudo`, `firewalld` instead of `ufw` (`sudo firewall-cmd --permanent --add-service=ssh && sudo firewall-cmd --reload`), and `dnf install -y dnf-automatic` for automatic updates. The SSH service is called `sshd`.

## That's it

Your server is updated, has a personal admin user, accepts only key logins, has a firewall and patches itself. Now install what you came for — a web server, Docker, a game server, your app.

---

Need a VPS? [Vagocat VPS](https://vagocat.com/vps-hosting) gives you full root access on Ubuntu, Debian, AlmaLinux or Windows Server, from $3.45/month — and real people to help when you're stuck.
