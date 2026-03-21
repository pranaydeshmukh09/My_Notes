# Linux Log Analysis (DevOps Notes)

## 1. What are Logs?
Logs are system-generated files that record events, activities, errors, and user actions.

They are used for:
- Debugging issues
- Monitoring system health
- Security auditing
- Performance analysis

----------------------------------------------

## 2. Default Log Directory
Most Linux logs are stored in:

```bash
/var/log/
```

----------------------------------------------

## 3. Important Linux Log Files

| Log File | Description |
|--------|------------|
| `/var/log/syslog` | General system activity (Debian/Ubuntu) |
| `/var/log/messages` | System messages (RHEL/CentOS) |
| `/var/log/auth.log` | Authentication logs (login, sudo, SSH) |
| `/var/log/kern.log` | Kernel messages |
| `/var/log/dpkg.log` | Package installation/removal |
| `/var/log/boot.log` | System boot logs |
| `/var/log/faillog` | Failed login attempts |
| `/var/log/lastlog` | Last login information |

----------------------------------------------

## 4. Web Server Logs

### Apache Logs
```bash
/var/log/apache2/access.log
/var/log/apache2/error.log
```

### Nginx Logs
```bash
/var/log/nginx/access.log
/var/log/nginx/error.log
```

----------------------------------------------

## 5. Basic Log Viewing Commands

### View entire log file
```bash
cat file.log
```

### View large logs safely
```bash
less file.log
```

### View last lines
```bash
tail file.log
```

### Live log monitoring
```bash
tail -f file.log
```

----------------------------------------------

## 6. Searching Logs

### Search keyword
```bash
grep "error" syslog
```

### Case-insensitive search
```bash
grep -i "failed" auth.log
```

### Search with line numbers
```bash
grep -n "error" syslog
```

----------------------------------------------

## 7. Counting Log Entries

### Count keyword occurrences
```bash
grep "error" syslog | wc -l
```

### Count failed logins
```bash
grep "Failed password" /var/log/auth.log | wc -l
```

----------------------------------------------

## 8. Time-Based Log Analysis

### Search logs by date
```bash
grep "Feb 6" syslog
```

### Last 50 log entries
```bash
tail -n 50 syslog
```

----------------------------------------------

## 9. Combining Commands (Pipes)

### Find 404 errors in access logs
```bash
grep "404" access.log
```

### Errors related to nginx
```bash
cat syslog | grep nginx
```

----------------------------------------------

## 10. Service Log Analysis

### Restart service and monitor logs
```bash
sudo systemctl restart nginx
tail -f /var/log/nginx/error.log
```

### Check service status
```bash
systemctl status nginx
```

----------------------------------------------

## 11. Authentication & Security Logs

### Failed SSH login attempts
```bash
grep "Failed password" /var/log/auth.log
```

### Successful logins
```bash
grep "Accepted password" /var/log/auth.log
```

----------------------------------------------

## 12. Log Rotation (Introduction)

Log rotation prevents logs from becoming too large.

### Configuration file
```bash
/etc/logrotate.conf
```

### Log rotation directory
```bash
/etc/logrotate.d/
```

----------------------------------------------

## 13. Common Log Levels

| Level | Meaning |
|------|--------|
| INFO | Normal operation |
| WARN | Warning, not critical |
| ERROR | Error occurred |
| CRITICAL | Serious issue |
| DEBUG | Debug information |

----------------------------------------------

## 14. Real-World Troubleshooting Flow

1. Identify affected service
2. Locate related log file
3. Use `tail -f` during issue reproduction
4. Search errors using `grep`
5. Take action based on log message

----------------------------------------------

## 15. Interview-Important Commands Summary

```bash
cat
less
tail
tail -f
grep
wc
systemctl
```

----------------------------------------------

## 16. Best Practices

- Never delete logs blindly
- Always analyze before restarting services
- Monitor logs in real time during deployments
- Keep logs secure (permission matters)

----------------------------------------------
