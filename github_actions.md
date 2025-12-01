# Introdução ao GitHub Actions

GitHub Actions é uma ferramenta de automação integrada ao GitHub que permite executar scripts e pipelines automaticamente em resposta a eventos no repositório. Ele possibilita criar workflows que são disparados por ações como push, commit, criação de issues, execução de migrations, abertura de pull requests, entre outras.

Um dos usos mais comuns do GitHub Actions é automatizar o deploy de aplicações.<br>
Por exemplo: quando um merge é feito na branch main ou master, um workflow pode ser configurado para realizar o deploy automaticamente, eliminando a necessidade de fazer esse processo manualmente.

Os arquivos de automação devem ser colocados na pasta <strong>.github/workflows </strong>, pois é nela que o GitHub identifica que os arquivos YAML pertencem a pipelines que ele deve executar.

Em resumo, o GitHub Actions é amplamente utilizado para:

- Automatizar deploys;
- Rodar testes a cada commit;
- Validar código (lint, build);
- Executar scripts de integração e migração;
- Criar rotinas automáticas baseadas em eventos do repositório.

Isso torna o desenvolvimento mais rápido, confiável e padronizado.

<br><br>
<h3>Referências Utilizadas na Construção deste Material:</h3>
https://docs.github.com/pt/actions/get-started/understand-github-actions
https://www.redhat.com/pt-br/topics/devops/what-is-ci-cd
http://medium.com/@habbema/github-actions-2d1e016a9cee
https://www.youtube.com/watch?v=df_WMXk7JxE
