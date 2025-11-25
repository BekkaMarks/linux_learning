# 📌 Comandos básicos e suas funcionalidades
### new-site
> O comando new-site irá cria um site dentro do ambiente bench. Cria uma nova basta dentro de `./sites`
com todas as informações e criando juntamente um novo banco de dados no <strong>SGBD</strong> com todos os módulos e tipos de documento do Frappe instalados.
```bash
bench new-site {site}
```

O <strong><i>Sistema de Gestão de Bases de Dados (SGBD)</i></strong> ou <strong><i>Data Base Management System (DBMS)</i></strong> é um conjunto de programas de computador (softwares) utilizado para administrar, organizar e manipular bancos de dados.<br>

### -- site

> No frappe é possível ter mais de um site dentro de um mesmo bench, para garantir que o comando execute no site certo,
> utilizamos o comando:

```bash
bench --site nome_do_site comando
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










<br><br><br><br><br><br><br><br>
https://docs.frappe.io/framework/v14/user/en/bench/reference/new-site
https://docs.frappe.io/framework/user/en/bench/frappe-commands
https://docs.frappe.io/framework/user/en/bench/bench-commands
