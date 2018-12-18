# Logrotate

logrotate is designed to ease administration of systems that generate large numbers of log files. It allows automatic rotation, compression, removal, and mailing of log files. Each log file may be handled daily, weekly, monthly, or when it grows too large.

Normally, logrotate is run as a daily cron job. 

Rotating log files is important for several reasons. First, you probably don't want older log files eating up too much of your disk space. Second, when you need to analyze log data, you probably don't want those log files to be extremely large and cumbersome. And last, organizing log files by date probably makes spotting and analyzing changes quite a bit easier




### Command: /bin/kill -HUP `cat /var/run/syslogd.pid 2> /dev/null` 2> /dev/null || true

Explaination: send SIGHUP to syslogd discard all error messages and return true if succeded.

1. /bin/kill -HUP <PID> - sends SIGHUP signal to process identified <PID>. Sending this signal to deamons (or services if you prefer) usually instructs them to reread (read again) their configuration
2. cat /var/run/syslogd.pid 2> /dev/null - reads the /var/run/syslogd.pid file (which contains PID of the syslogd daemon) and prints it to standard output (file descriptor = 0 (zero)). The 2> /dev/null part of it redirects standard error stream (file descriptor = 2 (two)) to /dev/null to discard all error messages that occured while reading /var/run/syslogd.pid
3. /dev/null is a special device file that discards (ignores) everything that is written to it (like a bottomless well). Sometimes used to discard error messages (like in your case here).

Reference: 
[1] https://linux.die.net/man/8/logrotate
[2] https://www.networkworld.com/article/3218728/linux/how-log-rotation-works-with-logrotate.html
[3] https://unix.stackexchange.com/questions/440004/why-is-kill-hup-used-in-logrotate-in-rhel-is-it-necessary-in-all-cases
[4] https://unix.stackexchange.com/questions/33447/why-we-should-use-create-and-copytruncate-together
