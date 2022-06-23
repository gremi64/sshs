# sshs

<a href="https://repology.org/project/sshs/versions">
    <img src="https://repology.org/badge/vertical-allrepos/sshs.svg" alt="Packaging status" align="right">
</a>

Terminal user interface for SSH.  
It uses `~/.ssh/config` to list and connect to hosts.

<br>

[![example](https://i.imgur.com/iPmiEVU.gif)](https://asciinema.org/a/465800)

# Requirements
You need to have `ssh` and `sshpass` installed and accessible from your terminal.

# How to install
## From sources
Install golang : https://go.dev/doc/install

Then
```bash
git clone --branch sshpass https://github.com/gremi64/sshs.git
cd sshs
make
sudo make install
```

Create `.sshpassfile`, type your password, end with `Ctrl+C`
```bash
cat - > ~/.sshpassfile
```

# Troubleshooting
## [...]/.ssh/config: no such file or directory
- Check if you have `~/.ssh/config` file
- If you don't, create it with `touch ~/.ssh/config`

If you want to use another SSH config file, you can use the `--config` option.

Here's a sample `~/.ssh/config` file:
```nginx
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_rsa

Host "My server"
  HostName server1.example.com
  User root
  Port 22

Host "Go through Proxy"
  HostName server2.example.com
  User someone
  Port 22
  ProxyCommand ssh -W %h:%p proxy.example.com
```

You can check the [OpenBSD `ssh_config` reference](https://man.openbsd.org/ssh_config.5) for more information on how to setup `~/.ssh/config`.

