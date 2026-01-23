# 🐘 Introdução ao PostgreSQL

PostgreSQL é um <strong>banco de dados relacional de código aberto</strong> que oferece suporte a recursos <strong>objeto-relacionais</strong>, como tipos definidos pelo usuário, herança e funções personalizadas.
Ele segue rigorosamente o modelo <strong>ACID</strong> (Atomicidade, Consistência, Isolamento e Durabilidade), garantindo segurança e integridade dos dados mesmo em cenários de falhas.

Para otimizar a recuperação de informações, o PostgreSQL utiliza <strong>índices</strong>, que nada mais são do que <strong>cópias organizadas de partes de uma tabela</strong>, permitindo buscas muito mais rápidas.
São semelhantes ao índice no final de um livro, que ajuda a encontrar um item sem precisar percorrer o livro inteiro.

O PostgreSQL oferece diferentes tipos de índices, como:
- <strong>B-tree</strong> (padrão e mais utilizado)
- <strong>Hash</strong>
- <strong>GIN</strong> (ideal para JSONB e arrays)
- <strong>GiST</strong>
- <strong>BRIN</strong> (ótimo para tabelas muito grandes)

O PostgreSQL usa descrições chamadas <strong>schemas</strong> para organizar a estrutura dos dados.
Um schema é o conjunto de tabelas, índices, funções e outros objetos dentro do banco de dados, e o PostgreSQL suporta múltiplos schemas sem conflito entre eles.

Além disso, o PostgreSQL é altamente <strong>extensível</strong>: é possível criar tipos de dados próprios, operadores, linguagens de função (como PL/pgSQL e PL/Python) e até instalar extensões como <strong>PostGIS</strong>.

Em cenários com múltiplos acessos simultâneos, o PostgreSQL gerencia a concorrência por meio do <strong>MVCC</strong> (Controle de Concorrência Multiversão).
Isso significa que:
- <strong>leituras não bloqueiam gravações</strong>, e
- <strong>gravações não bloqueiam leituras</strong>.

Esse modelo garante alto desempenho, reduz bloqueios e melhora o isolamento entre transações.

Outro componente fundamental é o <strong>WAL (Write-Ahead Logging)</strong>, um registro de todas as operações que garante durabilidade: antes de qualquer modificação ser escrita no disco, ela é registrada no WAL para que o banco possa ser recuperado em caso de queda inesperada.

O PostgreSQL conta ainda com diversos tipos de dados avançados, incluindo:
- <strong>JSON e JSONB</strong> (com performance excepcional)
- <strong>Arrays</strong>
- <strong>Tipos de faixa</strong> (range types)
- <strong>UUID</strong>
- <strong>Tipos geométricos</strong>

## Instalação
Os comandos abaixo realizam apenas a instalação padrão do PostgreSQL, incluindo:
- instalação dos pacotes básicos;
- ativação automática do serviço;
- criação do usuário padrão postgres;
- permissão de acesso local ao banco via sudo -u postgres psql.
 
```bash
sudo apt update
sudo apt install postgresql postgresql-contrib
```
Após a instalação, é possível validar o serviço e acessar o banco de dados:
```bash
# Verifica se o PostgreSQL está em execução
sudo systemctl status postgresql

# Acessa o banco como usuário postgres
sudo -u postgres psql
```
Faça a alteração da senha:
```bash
ALTER USER postgres PASSWORD 'nova-senha';
```

> <strong>Notas:</strong><br><br>
> MVCC — Recurso avançado de banco de dados que cria versões dos registros para permitir leitura e escrita simultâneas com segurança.
> Com o MVCC, vários usuários podem consultar e modificar dados ao mesmo tempo sem comprometer a integridade do banco.
> Principais vantagens:
> - Cria versões dos registros para leitura e escrita simultâneas
> - Evita bloqueios entre leituras e gravações
> - Mantém isolamento entre transações
> - Melhora o desempenho em ambientes com muitos usuários
> 
> B-tree — Estrutura de índice baseada em árvore balanceada. Mantém os dados organizados de forma ordenada, permitindo buscas rápidas mesmo em tabelas grandes. É o tipo de índice padrão no PostgreSQL por ser eficiente na maioria das consultas.<br>
> Estrutura Interna:<br>
> - Nó Raiz: ponto inicial da busca; contém chaves que direcionam para outros nós.
> - Nós Internos: organizam as chaves e definem o caminho até os dados; funcionam como intermediários.
> - Nós Folha: armazenam as chaves indexadas e ponteiros para as linhas da tabela.
> - Balanceamento: quando um nó enche, ele se divide; isso mantém a árvore sempre rasa e rápida para buscar.
> 
> JSON e JSONB (armazenamento flexível em formato documento)
Permitem guardar dados sem estrutura fixa e consultar campos internos com facilidade. O JSONB, em especial, oferece alto desempenho em buscas e indexação.
> - Armazenamento sem esquema rígido
> - Consulta eficiente a campos internos
> - Indexação avançada (GIN)
> - Ótimo para integrações e APIs
>
> Arrays (listas diretamente no banco)
> Possibilitam armazenar múltiplos valores em uma única coluna, com suporte nativo a buscas e operadores.
> - Múltiplos valores no mesmo campo
> - Operadores poderosos (@>, <@, &&)
> - Boa performance com indexação GIN
> - Simplificam modelos mais complexos
>
> Tipos de Faixa — Range Types (representação de intervalos)
> Usados para datas, números e outros valores contínuos, permitindo detectar sobreposição, inclusão e lacunas.
> - Representam intervalos (ex.: daterange, int4range)
> - Detectam conflitos automaticamente
> - Consultas rápidas com índices GiST/Sp-GiST
> - Ideais para reservas, períodos e escalas
>
> UUID (identificador único universal)
> Tipo nativo para chaves únicas distribuídas, sem riscos de colisão e sem depender de sequência incremental.
> - Exclusivo e globalmente único
> - Reduz problemas em sistemas distribuídos
> - Ótimo para evitar incrementos previsíveis
> - Suporte nativo a geração (gen_random_uuid())
>
> Tipos Geométricos (modelagem espacial básica)
> Permitem armazenar pontos, linhas, polígonos e áreas diretamente no banco.
> - Representação nativa de formas geométricas
> - Operadores para distância, área e interseção
> - Índices GiST para performance
> - Úteis em mapas, coordenadas e rotas

<br><br>

<h3>📚 Referências Utilizadas na Construção deste Material:</h3> 
https://cloud.google.com/discover/what-is-postgresql <br> 
https://www.ibm.com/think/topics/postgresql <br> 
https://aws.amazon.com/pt/compare/the-difference-between-mysql-vs-postgresql/ <br> 
https://www.postgresql.org/download/linux/ubuntu/ <br> 
https://www.hostinger.com/br/tutoriais/instalar-postgresql-ubuntu <br> 
https://www.vivaolinux.com.br/dica/Instalando-o-servidor-PostgreSQL-no-Linux <br> 
https://serverspace.com.br/support/glossary/mvcc/ <br>
https://serverspace.com.br/support/glossary/b-tree/ <br>
https://pt.stackoverflow.com/questions/101065/o-que-s%C3%A3o-os-%C3%ADndices-b-tree-hash-gist-e-gin <br>
