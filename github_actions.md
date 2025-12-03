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

> <strong>Pipelines:</strong> São sequências de etapas automatizadas executadas em ordem definida, garantindo que processos — como testes, validações, builds ou deploys — aconteçam de forma padronizada e sem intervenção manual. Em outras palavras, é qualquer cadeia de tarefas automatizadas organizada em etapas.
<br><br>
> <strong>Pipelines de CI/CD:</strong> São pipelines específicos usados no desenvolvimento de software para validar, testar, construir e implantar uma aplicação sempre que ocorre uma alteração no código, garantindo integração e entrega contínuas de forma segura e padronizada. <br>
> - CI (Continuous Integration): rodar testes, validar código, compilar, fazer lint.<br>
> - CD (Continuous Delivery/Deployment): gerar build, publicar artefatos, realizar o deploy.<br><br>
> 
><strong>Workflow:</strong>
> É um fluxo automatizado de tarefas que o GitHub Actions executa quando um evento ocorre (como push, commit, merge ou abertura de PR). Cada workflow define quando será executado e o que deve acontecer.<br><br>
>
> <strong>Deploy:</strong>
>Deploy é o processo de colocar uma aplicação em produção, tornando a versão atualizada disponível para os usuários. No GitHub Actions, o deploy geralmente é automatizado para rodar após um merge na branch principal.
<br><br>
> <strong>Lint:</strong>
> Ferramenta de análise de código estática usada para sinalizar erros de programação, bugs, erros estáticos e construções suspeitas.

<br><br>
<h3>Referências Utilizadas na Construção deste Material:</h3>
https://docs.github.com/pt/actions/get-started/understand-github-actions
https://www.redhat.com/pt-br/topics/devops/what-is-ci-cd
http://medium.com/@habbema/github-actions-2d1e016a9cee
https://www.youtube.com/watch?v=df_WMXk7JxE
