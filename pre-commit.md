# Pre-commit

## O que é?

**Pre-commit** é uma ferramenta que automatiza a execução de verificações e tarefas específicas no código-fonte antes que ele seja comprometido em um sistema de controle de versão, como o Git.  Atua como uma linha de defesa inicial, impedindo que código inadequado, mal formatado ou com erros chegue ao repositório. 

## Por que usar?

- ✅ **Prevenção antecipada** - Detecta problemas antes do commit
- 🔍 **Verificações automáticas** - Lint, formatação, testes e validações de segurança
- 🤝 **Consistência na equipe** - Todos seguem as mesmas regras automaticamente
- 📦 **Configuração compartilhada** - Arquivo `.pre-commit-config.yaml` versionado com o projeto

## Contexto:  Hooks

Para entender melhor o pre-commit, é importante conhecer os conceitos relacionados:

**Script Hooks**: Scripts executados automaticamente quando um evento específico acontece em um sistema (mudanças de estado, atualizações de dados, ciclo de vida de componentes, etc.).

**Git Hooks**: Scripts executados com automação toda vez que um evento específico ocorre em um repositório do Git. Eles permitem personalizar o comportamento interno do Git e acionar ações personalizáveis em pontos-chave do ciclo de vida do desenvolvimento. 

**Pre-commit**: Gerencia e padroniza especificamente hooks do tipo `pre-commit`, organizando múltiplos hooks de forma declarativa e facilitando o versionamento e compartilhamento entre a equipe.

## 📚 Referências

- 📖 [Documentação Oficial](https://pre-commit.com/#installation)
- 📝 [Tutorial Prático](https://medium.com/@habbema/pre-commit-315db54ef2d8)
- 🎥 [Vídeo Prático](https://www.youtube.com/watch?v=ObksvAZyWdo).
