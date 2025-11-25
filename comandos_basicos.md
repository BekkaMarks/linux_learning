# 📌 Comandos básicos e suas funcionalidades
### new-site
>O comando bench new-site criará um novo site dentro do ambiente Bench. Ele gera uma nova pasta dentro de `./sites` com todas as informações necessárias e também cria um novo banco de dados no SGBD, já com todos os módulos e tipos de documento do Frappe instalados.

```bash
bench new-site {nome_site}
```

➜ O <strong><i>Sistema de Gestão de Bases de Dados (SGBD)</i></strong> ou <strong><i>Data Base Management System (DBMS)</i></strong> é um conjunto de programas de computador (softwares) utilizado para administrar, organizar e manipular bancos de dados.<br>

### -- site

> No frappe é possível ter mais de um site dentro de um mesmo bench, para garantir que o comando execute no site certo,
> utilizamos o comando:

```bash
bench --site {nome_site} comando
```

### build
> Utilizado para compilar e gerar os arquivos estáticos (assets) do sistema — como CSS, JavaScript, SCSS, imagens, arquivos minificados e os bundles usados pelo frontend (Desk, Website, etc.).
Ele pega os arquivos-fonte de cada app e gera os pacotes finais dentro da pasta: `sites/assets/`.

```bash
bench build
```

### migrate
> Aplica todas as atualizações pendentes do Frappe/ERPNext no site, sincronizando DocTypes, banco de dados, patches, traduções e configurações relacionadas aos apps instalados.

```bash
bench migrate
```

### update
> Comando mais completo e pesado comparado ao migrate. Ele inclui o migrate, mas também executa outras tarefas importantes, como atualizar o código dos apps, instalar dependências, recompilar assets e reiniciar serviços do Bench.

```bash
bench update
```

### restart
> Reinicia processos que fazem a instância frappe/ERPNext (web, supervisor e systemd). Ele Possui alguns comportamentos distintos dependendo de como esta configurado o bench.<br><br>
> <strong>Comportamento por ambiente:</strong><br>
> 1 - Produção:
>     Delega ao supervisor ou systemd (faz o restart dos serviços configurados).<br>
> 2 - Desenvolvimento:
>     Reinicia os processos gerenciados por bench start/Procfile.
 
```bash
bench restart
```

### backup
> O comando bench backup cria um backup completo do site, incluindo:
> - Banco de dados: gera um arquivo .sql.gz com todas as tabelas e dados.
> - Arquivos públicos: compacta o conteúdo de `public/files`.
> - Arquivos privados: compacta o conteúdo de `private/files`.
> Ele garante que você possa restaurar o site exatamente como estava caso ocorra falha, migração ou corrupção de dados.

```bash
bench --site {nome_site} backup
```

### restore
> Restaura um backup completo de um site Frappe/ERPNext.
> O comando substitui inteiramente o banco de dados e os arquivos do site pelo conteúdo do backup especificado — ou seja, o site volta exatamente ao estado do momento do backup.

```bash
bench --site {nome_site} restore {path_do_backup_sql}
```

### drop-site
> Remove definitivamente o site do Frappe/ERPNext. Ele apaga o banco de dados do site, remove a pasta `sites/{site}` e elimina todas as configurações do site no bench.<br>
> Importante:
> É um comando destrutivo. Depois de executado, não há como recuperar o site, a menos que exista um backup.

```bash
bench drop-site {nome_site} 
```

### install-app
> Instala um aplicativo em um site Frappe/ERPNext, criando as tabelas, configurações e dependências necessárias no banco de dados.
> - Registra o app no site.
> - Executa as migrações do app (criação de DocTypes, tabelas, patches etc.).
> - Ativa o app para uso no site.

```bash
bench --site {nome_site} install-app {nome_do_app}
```


<br><br><br><br><br><br><br><br>
https://docs.frappe.io/framework/v14/user/en/bench/reference/new-site
https://docs.frappe.io/framework/user/en/bench
https://docs.frappe.io/framework/user/en/bench/frappe-commands
https://docs.frappe.io/framework/user/en/bench/bench-commands
https://discuss.frappe.io/t/frappe-bench-backup-and-restore-guide/148270
https://docs.frappe.io/framework/user/en/bench/reference/uninstall-app
https://docs.frappe.io/framework/user/en/bench/resources/bench-commands-cheatsheet
