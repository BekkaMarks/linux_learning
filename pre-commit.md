## O que são Script Hooks?

**Script hooks** são scripts executados automaticamente quando um evento específico acontece em um sistema.  Podem ser utilizados em diversas aplicações:  mudanças de estado, atualizações de dados, ciclo de vida de componentes, entre outros.

## Git Hooks

**Git hooks** são scripts executados com automação toda vez que um evento específico ocorre em um repositório do Git. Eles deixam você personalizar o comportamento interno do Git e acionar ações personalizáveis em pontos-chave do ciclo de vida do desenvolvimento.

## Pre-commit

**Pre-commit** é uma ferramenta que automatiza a execução de verificações e tarefas específicas no código-fonte antes que ele seja comprometido em um sistema de controle de versão, como o Git.  Atua como uma linha de defesa inicial, impedindo que código inadequado, mal formatado ou com erros chegue ao repositório.

### Por que usar? 

- ✅ **Prevenção antecipada** - Detecta problemas antes do commit
- 🔍 **Verificações automáticas** - Lint, formatação, testes e validações de segurança
- 🤝 **Consistência na equipe** - Todos seguem as mesmas regras automaticamente
- 📦 **Configuração compartilhada** - Arquivo `.pre-commit-config.yaml` versionado com o projeto

### Entendendo as Diferenças

**Script Hook** (conceito genérico):
- Script executado automaticamente em eventos de sistema
- Aplicável em diversos contextos além do Git

**Git Hook** (específico do Git):
- Script que personaliza o comportamento do Git
- Executado em pontos-chave do ciclo de desenvolvimento
- Configuração manual e local

**Pre-commit** (ferramenta):
- Gerencia e padroniza hooks do tipo `pre-commit`
- Organiza múltiplos hooks de forma declarativa
- Facilita versionamento e compartilhamento entre a equipe

<h3>Referências Utilizadas na Construção deste Material:</h3>
- 📖 [Documentação Oficial](https://pre-commit.com/#installation)<br>
- 📝 [Tutorial Prático](https://medium.com/@habbema/pre-commit-315db54ef2d8)
