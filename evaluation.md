# my evaluations awnsers

**Como uma máquina virtual funciona?**

Uma máquina virtual é um software que simula um computador físico. Ela pode ser usada para executar um sistema operacional diferente do que está instalado na máquina física. Com uma ferramenta chamada hypervisor, é possível criar várias máquinas virtuais em um único computador físico. Cada máquina virtual pode executar seu próprio sistema operacional, como Windows, Linux, etc.

**Principais diferenças entre Rocky e Debian**

Rocky é um sistema operacional voltado para servidores, enquanto o Debian é um sistema operacional voltado para desktops. O Rocky é baseado no Red Hat Enterprise Linux, enquanto o Debian é baseado no Debian GNU/Linux. O Rocky é um sistema operacional comercial, enquanto o Debian é um sistema operacional gratuito e de código aberto.

**qual é o propósito do das máquinas virtuais?**

O propósito das máquinas virtuais é permitir que um computador execute vários sistemas operacionais ao mesmo tempo. Isso é útil para testar software em diferentes sistemas operacionais, ou para executar vários sistemas operacionais em um único computador.

**qual a diferença entre apt e APPArmor?**

O apt é um gerenciador de pacotes usado para instalar e atualizar software no Debian. O AppArmor é um sistema de segurança que restringe o acesso de um programa a determinados arquivos, diretórios e funcionalidades do computador como o acesso a internet por exemplo.

**Como o LVM funciona?**

O LVM é um sistema de gerenciamento de volumes lógicos que permite que você crie partições lógicas em um disco rígido. Ele permite que você crie partições lógicas maiores do que o tamanho físico do disco rígido. Ele também permite que você crie partições lógicas em vários discos rígidos.

```bash
    # check if ufw service is running
    service ufw status
    # check if ssh is running
    service ssh status
    # check the current system is installed
    uname -a
    # check the current system is installed
    cat /etc/os-release

    # check groups of a user
    groups username
    # create a user
    adduser username

    vim /etc/login.defs
    vim /etc/security/pwquality.conf

    # create a group
    addgroup groupname

    # add user to group
    usermod -aG groupname username

    # check user password policy
    chage -l username

    # change hostname of the machine
    hostnamectl set-hostname newhostname
    # see my Ip
    hostname -I

    # check partitions
    lsblk

    # check ufw status
    ufw status

    # allow port
    ufw allow portnumber

    #check ssh port
    netstat -tulpn | grep ssh


    #see my cron jobs
    crontab -l

```
