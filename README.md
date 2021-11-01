# What's Going On Here?

This is currently a bash script that forwards a set of ports to a remote location using SSH.
Eventually this will all be wrapped up in a nice Rust program with a TUI, but we aren't there just yet!

This could also use Wireguard and iptables as a forwarding backend someday?

# What Needs Doing?

1) Ansible playbooks should be written to set up both the gateway server and computer to be forwarded.
The server needs to have a forwarding-capable `ssh` server installed and `GatewayPorts yes` (in `sshd_config` for openssh)
2) The client needs to authenticate with the remote server and copy over a public key
3) Future logins are done autonomously using the exchanged key and the local port is forwarded remotely
4) Any disconnections should result in a reattempt (probably with some form of gradual backoff applied)
