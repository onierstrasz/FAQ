
# LINUX FAQ

## Q How do I install updates?
```
sudo apt-get dist-upgrade
```

## Q How do I install software?
```
apt-get install ...
```

## Q How do you add a user xyz to the sudoers list? (Debian)
A Add xyz to the sudo line in `/etc/group`
```
sudo:x:27:oscar,niko,tverwaes,xyz
```

## Q How do I add a user?

This is the low-level one:
```
sudo useradd <user> -m
sudo passwd <user>
```
High-level interactive:
```
sudo adduser <user>
```
On calculon:
```
sudo realm permit -R campus.unibe.ch <campus-id>@campus.unibe.ch
```

## Q How do I give a user sudo rights? (Ubuntu)
```
sudo usermod -a -G sudo <user>
```
**NB:** `sudo` is the group name

## Q Who are the current users?
```
cat /etc/passwd
```

## Q How do I tell if I am running Debian or Ubuntu?
```
cat /etc/issue
```

## Q How do I install stuff?
```
sudo aptitude
```

## Q How do I restart the machine?
```
sudo shutdown -r now
```

## Q How do I shutdown the machine?
```
sudo shutdown -h now
```

## Q Why does ssh login always ask for a password even if I add my public key to the authorized keys?

Be sure the `.ssh` folder has 0700 access, and the authorized keys are not writeable by anyone else. Private keys not readable.

DSA is deprecated. Only use RSA. 
```
ssh-keygen -t rsa
```

Perhaps the file `/etc/ssh/sshd_config` is misconfigured.
```
RSAAuthentication yes
PubKeyAuthentication yes
```
	AuthorizedKeysFile %h/.ssh/authorized_keys
