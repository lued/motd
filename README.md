# Message of the Day

Collection of my 'Message of the Day' scripts.


### Requirements

  * update-motd
  * figlet & lolcat (for 10-display-name`)
  * fail2ban

### How do I set it up?

1. Copy the files you want in your MOTD to `/etc/update-motd.d/`. Make sure you have the `PrintMotd`
option set to `yes` in your /etc/ssh/sshd_config.

2. Delete certain scripts that do not pertain to you (smartd on a vm not showing, non-zpool.. etc..)

3. Test with `run-parts /etc/update-motd.d/` and edit your services and whatever else doesn't look right.

Note: You may have to delete /etc/motd contents as well (Debian + Ubuntu) as this defaults to Debian's TOS.


### How scripts function

The duplicate files are different versions of the same, use either one of them. E.g. `30-zpool-simple`
will not print usage bars.

The script `36-smartd` greps syslog for smartd entries to read temperature and last self-test result.
You have to enable smartd monitoring & run regular self-tests for it to display anything.

If you use `50-fail2ban` you should comment out the `compress` option in `/etc/logrotate.d/fail2ban`,
s.t. the logs are not compressed and can be grepped.
