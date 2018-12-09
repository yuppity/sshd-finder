# sshd-finder
Can't remember your home IP address? Dynamic DNS let you down? Fret not! Look
for the last known host key in `~/.ssh/known_hosts`, determine your ISP's AS
number, run

```
./sshd-finder <key fingerprint> <as number>
```

and wait.

Relies on the `ssh-keyscan` and `whois` executables.
