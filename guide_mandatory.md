# Mandatory part

what you need to do to complete the mandatory part

1. install utils
2. configure sudo
3. create an ssh server
4. create a strong password policy
5. create a new user and a group called `user42` and add your user to it
6. setup a cron that broadcast every 10 minutes shows system configuration

## Install useful libs

```bash
    apt-get install vim man git net-tools
```

## Configure sudo

1. install sudo

```bash
    apt-get install sudo
```

2. add your user to sudo group

```bash
    sudo usermod -aG sudo <username>
    # test if user is in sudo group
    groups <username>
```

3. edit sudoers file

```bash
    visudo
```

4. add the following line to the end of the file

```bash
    <username> ALL=(ALL) ALL
```

5. create your custom log file

```bash
    mkdir /var/log/sudo
    touch /var/log/sudo/sudo.log
```

6. edit sudoers file

```bash
    visudo
```

and add the following line to the end of the file or replace the existing ones

```bash
    Defaults     passwd_tries=3
    Defaults     badpass_message="SENHA ERRADA! TENTE NOVAMENTE!"
    Defaults     logfile="/var/log/sudo/sudo.log"
    Defaults     log_input
    Defaults     log_output
    Defaults     requiretty
```

test visudo file

```bash
    visudo -c
    # after that restart your terminal
    reboot
```

## Create an ssh server

before start make sure your VM is in bridged mode

1. install ssh and ufw

```bash
    apt-get install ssh ufw
```

enable ufw

```bash
    ufw enable
```

2. edit sshd_config file

```bash
    vim /etc/ssh/sshd_config
    Port 22 # change to 4242
```

check if port has changed

```bash
    service ssh restart
    service ssh status | grep port
```

3. enable 4242 port

```bash
    ufw allow 4242
    # check if port is open
    ufw status
    # remove 22 port if it is open
    ufw delete allow 22
```

4. connect to your VM using ssh

to know your VM ip address just type `hostname -I` in your VM terminal

```bash
    ssh <username>@<ip> -p 4242
```

## Create a strong password policy

1. install libpam-pwquality

```bash
    apt-get install libpam-pwquality
```

2. edit /etc/login.defs file

```bash
    vim /etc/login.defs
    PASS_MAX_DAYS 30
    PASS_MIN_DAYS 2
    PASS_WARN_AGE 7
```

3. edit /etc/security/pwquality.conf file

```bash
    difok = 7 #number of characters that must not be present in the old password.
    minlen = 10 #minimum len
    dcredit = -1 #min digits
    ucredit = -1 #min uppercase letters
    lcredit = -1 #min lowercase letters
    maxrepeat = 3 #max consecutive same characters
    usercheck = 1 #check if it contains user name in some form
    enforce_for_root #enforces pwquality checks on root user password
```

3. reboot your VM just type `reboot` in your VM terminal

4. change root password policy

```bash
    # check root password policy
    chage -l root
    # if changes are not applied
    chage -m 2 -M 30 root
    chage -m 2 -M 30 <username>
```

## Create a new user and a group called `user42` and add your user to it

```bash
    # create user
    adduser <username>
    # create group
    addgroup user42
    # add user to group user42
    usermod -aG user42 <username>
```

## Setup a cron that broadcast every 10 minutes shows system configuration

1. create a script.sh and save in /root
2. create a cronjob

```bash
    crontab -e
    */10 * * * * bash /root/script.sh | wall
```

3. test cronjob

```bash
    crontab -l
```

## END OF MANDATORY PART

[Go to bonus part](./guide_bonus.md)
