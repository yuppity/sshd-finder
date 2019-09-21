# sshd-finder
Can't remember your home IP address? Dynamic DNS let you down? Fret not! Look
for the last known host key in `~/.ssh/known_hosts`, determine your ISP's AS
number, run

```
./sshd-finder <partial key fingerprint> <as number>
```

and wait.

## Usage

```
usage: sshd-finder [-e] [-p port] [-k key_algo] fingerprint as_number

Scan ISP's IPv4 address space for an SSH server whose hostkey matches
a given host key fingerprint.

Options:
    -e, --exec-ks    use ssh-keyscan. sshds are still searched with sshd-finder
                     but actual key fetching is delegated to ssh-keyscan,
                     which does it more realiably than the simple key exchange
                     logic used in sshd-finder itself. another benefit is
                     support for wider range of kex algorithms and SSH
                     protocol versions.
    -p, --port=      port to scan (default: 22)
    -k, --key-algo=  host key algorithm (no effect with -e, --exec-ks).
                     allowed values:
                         "ecdsa" for ecdsa-sha2-nistp256 (default)
                         "ed25519" for ssh-ed25519
                         "rsa" for ssh-rsa

Arguments:
    fingerprint    complete or partial host key fingerprint
    as_number      ASN for the ISP whose network the sshd is on

```
