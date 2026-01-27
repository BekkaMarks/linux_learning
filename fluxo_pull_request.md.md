## 📌 Fluxo de Pull Request

Pull Request (PR) é o processo utilizado para propor, revisar e integrar código em um repositório de forma controlada, colaborativa e auditável.

Este documento descreve o ciclo de vida padrão de um Pull Request, aplicável a plataformas como GitHub, GitLab e Bitbucket.

```Text
┌───────────────────────────┐                       ┌───────────────────────────────────┐         ┌───────────────────────────────────────┐        ┌────────────────────────────┐
│     Criação do branch     │                       |    Abertura do Pull Request       |         | Validações automáticas (opcional)     |        |  Pós-merge (boas práticas) |
│  - Branch criado a partir |                       |  Comparação:                      |         |  - CI/CD                              |        | Deletar branch de feature  |
|  da base (man, develop).  │                       |    - origem: branch de feature    |         |  - Testes                             |        | Deploy                     |
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
