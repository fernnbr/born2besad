# Comandos Iniciais (Configuração)

```
shellsudo nano /etc/ssh/sshd_config
sudo nano /etc/sudoers.d/sudo_config
sudo nano /etc/login.defs
sudo nano /etc/pam.d/common-password
```

### Configuração prévia e serão verificados nas seguintes fases:


- /etc/ssh/sshd_config | **SSH section**
- /etc/sudoers.d/sudo_config | **SUDO section**
- /etc/login.defs e /etc/pam.d/common-password | **User section (password policy)**


# (1) Mapeamento dos Comandos por Seção:

#### Simple Setup

# Verificar interface gráfica

```
shellls /usr/bin/*session
```

# Verificar UFW

```
shellsudo ufw status
sudo service ufw status
```

## Verificar SSH

```
shellsudo service ssh status
```

## Verificar sistema operacional

```
shelluname -v
```

# User Section

## (2) Verificar grupos do usuário

```
shellgetent group sudo
getent group user42
```

## Criar novo usuário

```
shellsudo adduser name_user
```

## Criar grupo "evaluating"

```
shellsudo addgroup evaluating
```

## Adicionar usuário ao grupo

```
shellsudo adduser name_user evaluating
sudo getent group evaluating
```

# (3) Hostname and Partitions

## Verificar hostname

```
shellhostname
```

## Modificar hostname

```
shellsudo nano /etc/hostname
sudo nano /etc/hosts
sudo reboot
hostname
```

## Verificar partições

```
shelllsblk
```

# (4) SUDO Section

## Verificar instalação do sudo

```
shellwhich sudo
dpkg -s sudo
```

## Adicionar usuário ao grupo sudo

```
shellsudo adduser name_user sudo
getent group sudo
```

## Mostrar regras do sudo

```
shellsudo nano /etc/sudoers.d/sudo_config
```

## Verificar logs do sudo

```
shellcd /var/log/sudo
ls
cat sudo_config
sudo nano hello42world
cat sudo_config
```

## UFW Section

## Verificar instalação do UFW

```
shelldpkg -s ufw
sudo service ufw status
```

## Listar regras ativas

```
shellsudo ufw status numbered
```

## Adicionar/deletar regra porta 8080

```
shellsudo ufw allow 8080
sudo ufw status numbered
sudo ufw delete num_rule
sudo ufw status numbered
sudo ufw delete num_rule
sudo ufw status numbered
```

# (5) SSH Section

## Verificar SSH e porta 4242

```
shellwhich ssh
sudo service ssh status
```

## Testar login SSH

```
shellssh root@ip_machine -p 4242  # deve falhar
ssh usuário@ip_machine -p 4242  # deve funcionar
```

# (6) Script Monitoring Section

## Modificar tempo do cron

```
shellsudo crontab -u root -e
```

## Parar/iniciar script

```
shellsudo /etc/init.d/cron stop
sudo systemctl stop cron
sudo systemctl disable cron
sudo systemctl enable cron
sudo /etc/init.d/cron start
```

# Resumo da Ordem:

(1) Simple Setup (comandos 1-4)
(2) User (comandos 5-8)
(3) Hostname and Partitions (comandos 9-11)
(4) SUDO (comandos 12-15)
(5) UFW (comandos 16-18)
(6) SSH (comandos 19-20)
(7) Script Monitoring (comandos 21-22)
