Pull Request é o processo de propor, revisar e integrar código de forma controlada e colaborativa.

```Text
┌───────────────────────────┐                       ┌───────────────────────────────────┐         ┌───────────────────────────────────────┐        ┌──────────────────────────┐
│     Criação do branch     │                       |    Abertura do Pull Request       |         | Validações automáticas (opcional)     |        |       Pós-merge          |
│  - Branch criado a partir |                       |  Comparação:                      |         |  - CI/CD                              |        | Deletar branch de feature|
|  da base (man, develop).  │                       |    - origem: branch de feature    |         |  - Testes                             |        | Deploy                   |
└────────────┬──────────────┘                       |    - destino: branch principal    |         |  - Lint                               |        | Monitoramento            |
             |                                      |  PR nasce com status open ou draft|         |  - Build                              |        └──────────────────────────┘
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
