# 🔧 Instalação ERPNext (Ubuntu 22.04)

Este README descreve um fluxo prático para instalar o ERPNext em um servidor Ubuntu 22.04, incluindo a configuração do MariaDB. Substitua valores de exemplo (IP, porta, domínio, nomes) pelos seus.

> Observação: este guia assume Ubuntu 22.04 e que você executa comandos como `root` ou com `sudo`. Ajuste conforme necessário para outras distribuições.

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
Atualize pacotes:
```bash
sudo apt update && sudo apt upgrade
```

---

## Passo 3 — Criar usuário do sistema
Crie um usuário dedicado para a instalação:
```bash
sudo useradd -m -d /opt/erpnext -U -r -s /bin/bash erpnext
sudo usermod -aG sudo erpnext
```

---

## Passo 4 — Instalar dependências
Instale dependências necessárias:
```bash
sudo apt install -y python3-pip python3-dev python3.10-venv python3-testresources \
libffi-dev libssl-dev wkhtmltopdf gcc g++ make redis-server
```

---

## Passo 5 — Instalar Node.js e yarn
Adicione o repositório NodeSource e instale Node 16:
```bash
curl -sL https://deb.nodesource.com/setup_16.x | bash -
sudoapt install nodejs -y
node -v; npm -v
sudo npm install -g yarn
```

---

## Passo 6 — Instalar e configurar MariaDB
Instale o MariaDB:
```bash
sudo apt install mariadb-server mariadb-client
```

Edite o arquivo de configuração:
```bash
sudo nano /etc/mysql/mariadb.conf.d/50-server.cnf
```

Dentro do bloco `[mysqld]`, ajuste/adicione:
```ini
collation-server = utf8mb4_unicode_ci

innodb-file-format = barracuda
innodb-file-per-table = 1
innodb-large-prefix = 1
```

Reinicie e execute o script de segurança:
```bash
sudo systemctl restart mariadb
sudo mysql_secure_installation
```
Responda a todas as perguntas com "SIM" (S) e guarde a senha root do MySQL.

---

## Passo 7 — Instalar Bench e ERPNext
Troque para o usuário criado:
```bash
sudo su - erpnext
```

Em seguida, edite o arquivo .bashrc:
```bash
$ nano ~/.bashrc
```

Adicione a seguinte linha ao arquivo:
```bash
PATH=$PATH:~/.local/bin/
```
Salve o arquivo e, em seguida, ative a variável de ambiente com o seguinte comando abaixo:
```bash
$ source ~/.bashrc
```

Crie o diretório do bench e ajuste permissões:
```bash
# como root (ou usando sudo antes)
sudo mkdir -p /opt/bench
sudo chown -R erpnext:erpnext /opt/bench

cd /opt/bench
```

Clone e instale o bench (execução como `erpnext`):
```bash
git clone https://github.com/frappe/bench bench-repo
pip3 install --user -e bench-repo
```

Inicialize o bench:
```bash
bench init erpnext
```

Crie um novo site (substitua pelo seu domínio):
```bash
cd /opt/bench/erpnext
bench new-site erpnext.seudominio.com
```
O comando pedirá a senha do banco, administração e outras configurações. Forneça conforme sua política de segurança.

---

## Passo 8 — Configurar serviço e proxy reverso
Instale Nginx e Supervisor:
```bash
sudo apt install supervisor nginx -y
```

vamos instalar o frappe-bench e executar o comando abaixo.
```bash
$ sudo pip3 instalar frappe-bench
```

Em seguida, navegue até /opt/bench/erpnext e configure o ambiente de produção:
```bash
$ cd /opt/bench/erpnext 
$ sudo /opt/erpnext/.local/bin/bench setup production erpnext
```

---

## Referência
Guia base consultado:
- https://www.rosehosting.com/blog/how-to-install-erpnext-on-ubuntu-22-04/

---
