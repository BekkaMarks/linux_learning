# 🔧 Instalação ERPNext (Ubuntu 22.04)

Este README descreve um fluxo prático para instalar o ERPNext em um servidor Ubuntu 22.04, incluindo a configuração do MariaDB. Substitua valores de exemplo (IP, porta, domínio, nomes) pelos seus.

> Observação: este guia assume Ubuntu 22.04 e que você executa comandos como `root` ou com `sudo`. Ajuste conforme necessário para outras distribuições.
"conect como root ou sudo su - "
## Passo 1 — Conexão SSH
Conecte ao servidor:
```bash
ssh root@IP_Address -p Port_number
```

Verifique a versão do Ubuntu:
```bash
lsb_release -a
```

---

## Passo 2 — Atualizar o sistema
```bash
sudo su -
```
Atualize pacotes:
```bash
apt update && sudo apt upgrade
```

---

## Passo 3 — Criar usuário do sistema
Crie um usuário dedicado para a instalação:
```bash
useradd -m -d /opt/frappe -U -r -s /bin/bash frappe
usermod -aG sudo frappe
```
Lembre-se de adicionar uma senha utilizando passwd.

---

## Passo 4 — Instalar dependências
Instale dependências necessária
```bash
apt install -y python3-pip python3-dev python3.10-venv python3-testresources \
libffi-dev libssl-dev wkhtmltopdf gcc g++ make redis-server
```
Verifique na documentação oficial do Frappe se as dependências e versões estão corretas para a versão que você vai instalar: https://docs.frappe.io/framework/user/en/installation<br>

Em seguida instale pkg-config
```bash
apt install -y pkg-config
```
---

## Passo 5 — Instalar Node.js e yarn
Adicione o repositório NodeSource e instale Node 18:
```bash
curl -sL https://deb.nodesource.com/setup_18.x | bash -
```
ou
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
apt install nodejs -y
node -v; npm -v
npm install -g yarn
```

---

## Passo 6 — Instalar e configurar MariaDB

```bash
mkdir /etc/mysql/
mkdir /etc/mysql/mariadb.conf.d
nano my-cnf.conf

```

Cole esse arquivo dentro do terminal e depois crtl s + crtl x
```bash
#
# These groups are read by MariaDB server.
# Use it for options that only the server (but not clients) should see

# this is read by the standalone daemon and embedded servers
[server]

# this is only for the mysqld standalone daemon
[mysqld]
innodb_page_size=64K
innodb_default_row_format = dynamic
innodb_strict_mode = 0
innodb-file-format=barracuda
innodb-file-per-table=1
innodb-large-prefix=1
#
# * Basic Settings
#

#user                    = mysql
pid-file                 = /run/mysqld/mysqld.pid
basedir                  = /usr
#datadir                 = /var/lib/mysql
#tmpdir                  = /tmp

# Broken reverse DNS slows down connections considerably and name resolve is
# safe to skip if there are no "host by domain name" access grants
#skip-name-resolve

# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address            = 0.0.0.0

#
# * Fine Tuning
#

#key_buffer_size        = 128M
#max_allowed_packet     = 1G
#thread_stack           = 192K
#thread_cache_size      = 8
# This replaces the startup script and checks MyISAM tables if needed
# the first time they are touched
#myisam_recover_options = BACKUP
max_connections         = 10000
#table_cache            = 64

#
# * Logging and Replication
#

# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
# Recommend only changing this at runtime for short testing periods if needed!
#general_log_file       = /var/log/mysql/mysql.log
#general_log            = 1

# When running under systemd, error logging goes via stdout/stderr to journald
# and when running legacy init error logging goes to syslog due to
# /etc/mysql/conf.d/mariadb.conf.d/50-mysqld_safe.cnf
# Enable this if you want to have error logging into a separate file
#log_error = /var/log/mysql/error.log
# Enable the slow query log to see queries with especially long duration
#slow_query_log_file    = /var/log/mysql/mariadb-slow.log
#long_query_time        = 10
#log_slow_verbosity     = query_plan,explain
#log-queries-not-using-indexes
#min_examined_row_limit = 1000

# The following can be used as easy to replay backup logs or for replication.
# note: if you are setting up a replication slave, see README.Debian about
#       other settings you may need to change.
#server-id              = 1
#log_bin                = /var/log/mysql/mysql-bin.log
expire_logs_days        = 10
#max_binlog_size        = 100M

#
# * SSL/TLS
#

# For documentation, please read
# https://mariadb.com/kb/en/securing-connections-for-client-and-server/
#ssl-ca = /etc/mysql/cacert.pem
#ssl-cert = /etc/mysql/server-cert.pem
#ssl-key = /etc/mysql/server-key.pem
#require-secure-transport = on

#
# * Character sets
#

# MySQL/MariaDB default is Latin1, but in Debian we rather default to the full
# utf8 4-byte character set. See also client.cnf
character-set-server  = utf8mb4
collation-server = utf8mb4_unicode_ci
#
# * InnoDB
#

# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
# Most important is to give InnoDB 80 % of the system RAM for buffer use:
# https://mariadb.com/kb/en/innodb-system-variables/#innodb_buffer_pool_size
innodb_buffer_pool_size = 22G

# this is only for embedded server
[embedded]

# This group is only read by MariaDB servers, not by MySQL.
# If you use the same .cnf file for MySQL and MariaDB,
# you can put MariaDB-only options here
[mariadb]

# This group is only read by MariaDB-11.2 servers.
# If you use the same .cnf file for MariaDB of different versions,
# use this group for options that older servers don't understand
[mariadb-11.2]
```
```bash
cp my-cnf.conf /etc/mysql/mariadb.conf.d/50-server.cnf
```

Instale o MariaDB:
```bash
apt install mariadb-server mariadb-client

```

Reinicie e execute o script de segurança:
```bash
mysql_secure_installation
```
Responda a todas as perguntas com "SIM" (S) e guarde a senha root do MySQL.<br><br>

---

## Passo 7 — Instalar Bench e ERPNext
Troque para o usuário criado:
```bash
su - frappe
```

Em seguida, edite o arquivo .bashrc:
```bash
 nano ~/.bashrc
```

Adicione a seguinte linha ao arquivo:
```bash
PATH=$PATH:~/.local/bin/
```
Salve o arquivo e, em seguida, ative a variável de ambiente com o seguinte comando abaixo:
```bash
 source ~/.bashrc
```

Crie o diretório do bench e ajuste permissões:
```bash
sudo mkdir -p /opt/bench
sudo chown -R frappe:frappe /opt/bench

cd /opt/bench
```

Clone e instale o bench (execução como `frappe`):
```bash
git clone https://github.com/frappe/bench bench-repo
pip3 install --user -e bench-repo
```

Inicialize o bench:
```bash
bench init frappe-bench
```

Crie um novo site (substitua pelo seu domínio):
```bash
cd /opt/bench/frappe-bench/
bench new-site frappe.seudominio.com
```
Para verificar o dns: https://www.whatsmydns.net/<br><br>
O comando pedirá a senha do banco, administração e outras configurações. Forneça conforme sua política de segurança.

---

## Passo 8 — Configurar serviço e proxy reverso
Instale Nginx e Supervisor:
```bash
sudo apt install supervisor nginx -y
```

vamos instalar o frappe-bench e executar o comando abaixo.
```bash
 sudo pip3 install frappe-bench
```

Em seguida, navegue até /opt/bench/frappe e configure o ambiente de produção:
```bash
sudo bench setup production frappe
```
---

## Passo 9 — Configurando o Postman e instalação do certbot

Configuração do “Postman” (campos principais)

- Zone: parte final do domínio (ex.: max.com).
- Name: subdomínio/início do site (ex.: nomedosite).<br>
Resultado completo do host: Name + "." + Zone → nomedosite.max.com<br><br>
Para a instalação do certbot que irá ajudar a disponibilizar a porta de certificado:

```bash
sudo python3 -m venv /opt/certbot/
sudo /opt/certbot/bin/pip install certbot certbot-nginx
sudo ln -s /opt/certbot/bin/certbot /usr/bin/certbot
```
```bash
bench config dns_multitenant on
sudo -H bench setup lets-encrypt seu_dominio.com
```
Responda a todas as perguntas com "SIM" (S) exeto a mensagem de pedido de autorização (opt‑in) para usar/compartilhar seu e‑mail.

---
## Referência
Guia base consultado:
- https://www.rosehosting.com/blog/how-to-install-erpnext-on-ubuntu-22-04/

---
