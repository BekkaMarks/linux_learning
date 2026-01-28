## 📌 Fluxo de Pull Request

Pull Request (PR) é o processo utilizado para propor, revisar e integrar código em um repositório de forma controlada, colaborativa e auditável.

Este documento descreve o ciclo de vida padrão de um Pull Request, aplicável a plataformas como GitHub, GitLab e Bitbucket.

```Text
┌───────────────────────────┐                       ┌───────────────────────────────────┐         ┌───────────────────────────────────────┐        ┌────────────────────────────┐
│     Criação do branch     │                       |    Abertura do Pull Request       |         | Validações automáticas (opcional)     |        |  Pós-merge (boas práticas) |
│  - Branch criado a partir |                       |  Comparação:                      |         |  - CI/CD                              |        | Deletar branch de feature  |
|  da base (main, develop).  │                       |    - origem: branch de feature    |         |  - Testes                             |        | Deploy                     |
└────────────┬──────────────┘                       |    - destino: branch principal    |         |  - Lint                               |        | Monitoramento              |
             |                                      |  PR nasce com status open ou draft|         |  - Build                              |        └────────────────────────────┘
             ▼                                      └─────────────────┬─────────────────┘         | O PR pode ficar blocked se algo falhar|      
┌───────────────────────────┐                                         |                           └───────────────────┬───────────────────┘
|       Desenvolvimento     |                                         ▼                                               |
|   - Alteração no código   |                       ┌───────────────────────────────────┐                             ▼      
|   - Commits locais        |                       |   Revisão de código (code review) |           ┌─────────────────────────────────────┐
└────────────┬──────────────┘                       |  - Leitura do código              |           |           Decisão final             |
             |                                      |  - Comentários e sugestões        |           |  Dois caminhos possíveis:           |
             ▼                                      |  - Solicitação de mudanças        |           |  ✅ Merge                           |
┌───────────────────────────────────┐               └─────────────────┬─────────────────┘           |  - Código integrado á branch destino|
| Push para o repositório remoto    |                                 |                             |  - Estratégias comuns:              |
| - Envio do branch para o servidor |                                 ▼                             |     - merge commit                  | 
| - Ajustes incrementais            |               ┌───────────────────────────────────┐           |     - squash e merge                |
└───────────────────────────────────┘               |     Ajustes (se necessário)       |           |     - rebase e merge                |
                                                    |  Novos commits no mesmo branch    |           |   - PR fica merged                  |
                                                    |  Pr é atualizada automaticamente  |           |   ❌ Close                          |
                                                    └───────────────────────────────────┘           |      - PR encerrada sem merge       | 
                                                                                                    |      - Código não entra no projeto  |
                                                                                                    └─────────────────────────────────────┘
```
> <strong>Notas:</strong><br><br>
> CI/CD (Continuous Integration / Continuous Delivery ou Deployment) — Conjunto de automações que validam, testam e preparam ou realizam a entrega do código automaticamente a partir de eventos no >repositório (push, PR, merge).
> 
> Deploy — Processo de publicar uma versão do código já aprovada em um ambiente (servidor, container, nuvem, homologação ou produção), tornando-a efetivamente executável. Fluxo: [Pull Request → CI (testes, build, validações) → Merge → CD → Deploy]
>
> Squash — Estratégia de merge que consolida todos os commits de um Pull Request em um único commit na branch de destino, mantendo o histórico mais limpo e organizado.
