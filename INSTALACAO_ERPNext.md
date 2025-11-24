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
Instale o MariaDB:
```bash
apt install mariadb-server mariadb-client

```

criar o diretório (se necessário) e copiar o arquivo de configuração
```bash
mkdir -p /etc/mysql/mariadb.conf.d
cp /home/grv/my-cnf.conf /etc/mysql/mariadb.conf.d/50-server.cnf
```
Ou edite/crie o arquivo diretamente:
```bash
nano /etc/mysql/mariadb.conf.d/50-server.cnf
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
systemctl restart mariadb
mysql_secure_installation
```
Responda a todas as perguntas com "SIM" (S) e guarde a senha root do MySQL.<br><br>

Instale o bench no sudo e nomeie a instância como 'frappe-bench' (ex.: /opt/bench/frappe-bench) para indicar que pertence ao usuário/ambiente frappe.
```bash
bench init nome-bench 
```
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
# como root (ou usando sudo antes)
mkdir -p /opt/bench
chown -R frappe:frappe /opt/bench

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
cd /opt/bench/frappe
bench new-site frappe.seudominio.com
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
 sudo pip3 install frappe-bench
```

Em seguida, navegue até /opt/bench/frappe e configure o ambiente de produção:
```bash
cd /opt/bench/frappe 
sudo /opt/frappe/.local/bin/bench setup production frappe NO LUGAR DESSE:

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
sudo /opt/certbot/bin/pip install certbot certbot-nginx
sudo ln -s /opt/certbot/bin/certbot /usr/bin/certbot
bench config dns_multitenant on
sudo -H bench setup lets-encrypt seu_dominio.com
```
Responda a todas as perguntas com "SIM" (S) exeto a mensagem de pedido de autorização (opt‑in) para usar/compartilhar seu e‑mail.

---
## Referência
Guia base consultado:
- https://www.rosehosting.com/blog/how-to-install-erpnext-on-ubuntu-22-04/

---
