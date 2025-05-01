# Create Ubuntu WSL Distribution with Custom Name

`wsl --install Ubuntu --name SimpleDjangoApp`:

```ps
PS C:\Users\FlynntKnapp\Programming> wsl --install Ubuntu --name SimpleDjangoApp
Downloading: Ubuntu
Installing: Ubuntu
Distribution successfully installed. It can be launched via 'wsl.exe -d SimpleDjangoApp'
PS C:\Users\FlynntKnapp\Programming>
```

`wsl --list --verbose`:

```ps
PS C:\Users\FlynntKnapp\Programming> wsl --list --verbose
  NAME                 STATE           VERSION
* docker-desktop       Running         2
  NewSimpleFlaskApp    Stopped         2
  Ubuntu               Stopped         2
  SimpleDjangoApp      Stopped         2
PS C:\Users\FlynntKnapp\Programming>
```

`wsl.exe -d SimpleDjangoApp`:

```ps
PS C:\Users\FlynntKnapp\Programming> wsl.exe -d SimpleDjangoApp
Provisioning the new WSL instance SimpleDjangoApp
This might take a while...
Create a default Unix user account: flynntknapp
New password:
Retype new password:
passwd: password updated successfully
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

Welcome to Ubuntu 24.04.2 LTS (GNU/Linux 5.15.167.4-microsoft-standard-WSL2 x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

 System information as of Wed Apr 30 21:24:14 EDT 2025

  System load:  0.12                Processes:             32
  Usage of /:   0.1% of 1006.85GB   Users logged in:       0
  Memory usage: 4%                  IPv4 address for eth0: 172.21.189.255
  Swap usage:   0%


This message is shown once a day. To disable it please create the
/home/flynntknapp/.hushlogin file.
flynntknapp@DELL-DESKTOP:/mnt/c/Users/FlynntKnapp/Programming$
```

`cd ~`:

```bash
flynntknapp@DELL-DESKTOP:/mnt/c/Users/FlynntKnapp/Programming$ cd ~
flynntknapp@DELL-DESKTOP:~$
```

`mkdir Programming`:

```bash
flynntknapp@DELL-DESKTOP:~$ mkdir Programming
flynntknapp@DELL-DESKTOP:~$
```

`cd Programming/`:

```bash
flynntknapp@DELL-DESKTOP:~$ cd Programming/
flynntknapp@DELL-DESKTOP:~/Programming$
```

`sudo apt-get update && sudo apt-get upgrade`

```bash
flynntknapp@DELL-DESKTOP:~/Programming$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for flynntknapp:
.
.
.
Need to get 90.1 MB of archives.
After this operation, 1277 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
.
.
.
flynntknapp@DELL-DESKTOP:~/Programming$
```
