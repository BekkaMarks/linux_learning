# Gerando e configurando uma chave SSH para o GitHub

omo Este procedimento permite autenticar no GitHub via SSH, evitando o uso de usuário e senha a cada operação Git.

<strong>1. Gerar a chave SSH</strong>

Execute o comando abaixo, substituindo pelo e-mail usado no GitHub:
```bash
ssh-keygen -t ed25519 -C "email.git"
```

Pressione Enter para aceitar o caminho padrão, não precisa definir uma senha.

<strong>2. Iniciar o agente SSH</strong>
```bash
eval "$(ssh-agent -s)"
```
<strong>3. Adicionar a chave privada ao agente</strong>
```bash
ssh-add ~/.ssh/id_ed25519
```
<strong>4. Copiar a chave pública<br></strong>
Use o comando abaixo para visualizar a chave pública:

```bash
sudo cat ~/.ssh/id_ed25519.pub
```
Copie todo o conteúdo exibido e cole em GitHub → Settings → SSH and GPG keys → New SSH key.

<strong>5. Atualizar o repositório local</strong>

Após configurar a chave no GitHub, execute:
```bash
git fetch upstream
git pull
```
<br><br>
<h3>Referências Utilizadas na Construção deste Material:</h3>

https://docs.github.com/pt/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent
