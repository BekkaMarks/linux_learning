# 📦 Métodos de Armazenamento e Modelos de Bancos de Dados
Este material apresenta os principais modelos de armazenamento de dados utilizados em aplicações modernas, bem como conceitos essenciais relacionados a sistemas de gerenciamento de banco de dados e operações básicas.

## 🗂️ Bancos de Dados Relacionais (SQL)
Bancos relacionais organizam os dados em tabelas estruturadas (linhas e colunas), seguindo um esquema rígido definido previamente.

Esse modelo é ideal para cenários que exigem:
- Consistência forte
- Relacionamentos complexos entre dados
- Consultas SQL sofisticadas
- Integridade referencial

A estrutura tabular facilita entender como os dados se relacionam e permite operações avançadas como joins, agregações e transações ACID.

## 📚 Bancos de Dados Não Relacionais (NoSQL)
Bancos NoSQL oferecem maior flexibilidade, permitindo armazenar dados em diferentes formatos, como:
- Documentos (JSON)
- Chave-valor
- Colunas largas
- Grafos

Eles são indicados para:
- Dados não estruturados ou sem esquema fixo
- Escalabilidade horizontal (distribuição em múltiplos servidores)
- Grandes volumes de dados
- Aplicações que exigem alta performance e baixa latência

## 🧩 ORDBMS — Sistemas de Banco de Dados Objeto-Relacional
ORDBMS combinam características dos bancos relacionais tradicionais com recursos dos sistemas orientados a objetos.

Eles permitem:
- Criar tipos de dados personalizados
- Armazenar estruturas mais complexas
- Suportar herança, funções definidas pelo usuário e operadores próprios
- PostgreSQL é um exemplo clássico de ORDBMS.

## 🗄️ SGBD — Sistemas de Gerenciamento de Banco de Dados
Um SGBD é o software responsável por gerenciar o armazenamento, acesso, manipulação e segurança dos dados.

Ele atua como intermediário entre a aplicação e o banco, garantindo:
- Controle de permissões
- Integridade dos dados
- Eficiência em leitura e escrita
- Execução de transações
- Mecanismos de backup e recuperação

Exemplos: PostgreSQL, MySQL, MariaDB, Oracle, SQL Server, MongoDB.

## 🔄 CRUD
CRUD é o acrônimo para as quatro operações fundamentais realizadas em bancos de dados:

- Create (Criar)
- Read (Ler)
- Update (Atualizar)
- Delete (Deletar)

Essas operações representam a base da interação entre sistemas e dados, sendo usadas em praticamente qualquer aplicação que manipule informações.
