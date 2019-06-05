# Custom RPI Message of the Day for ssh

## About

<p align="center">
  <img src="https://github.com/gagle/raspberrypi-motd/blob/master/motd.png?raw=true"/>
</p>

This is a customised version of raspberrypi-motd. If you are looking to create your own custom MOTD, or if you are looking for the origional it is located at
https://github.com/gagle/raspberrypi-motd. Full credit goes to Gabriel Llamas (https://github.com/gagle) for the code.

The scriptis written in bash so requires no external packages to be installed.

Last update: 05/06/2019 (DD/MM/YYYY)

## Installation

Download and save the `motd.sh` bash script in the Raspberry Pi. Remember to add execution permissions and change the owner:

```bash
$ sudo chown root:root motd.sh
$ sudo chmod +x motd.sh
```

The following steps may vary depending on the OS. Arch Linux ARM is assumed.

- Autoexecute the script when the user logs in. There are multiple locations from where you can start the `motd.sh` script, for example using the `/etc/profile`. Save the `motd.sh` script in the directory `/etc/profile.d` and it will be executed after the login. More about [autostarting scripts](https://wiki.archlinux.org/index.php/Bash#Configuration_file_sourcing_order_at_startup).

- Remove the default MOTD. It is located in `/etc/motd`.
  
  ```bash
  $ sudo rm /etc/motd
  ```
  
- Remove the "last login" information. Disable the `PrintLastLog` option from the `sshd` service. Edit the `/etc/ssh/sshd_config` file and uncomment the line `#PrintLastLog yes`:
  
  ```bash
  $ sudo nano /etc/ssh/sshd_config
  ```
  
  Before:
  
  ```text
  #PrintLastLog yes
  ```
  
  After:
  
  ```text
  PrintLastLog no
  ```
  
  Restart the `sshd` service:
  
  ```bash
  $ sudo systemctl restart sshd
  ```

## Troubleshooting

Note: If you don't see the degree Celsius character correctly (`º`) make sure you have enabled a UTF8 locale ([Arch Linux locales](https://wiki.archlinux.org/index.php/locale)).

## Contributors

- Nathaniel Struselis - NathanielJS1541 on GitHub
- James Clarke        - revivedbear on GitHub