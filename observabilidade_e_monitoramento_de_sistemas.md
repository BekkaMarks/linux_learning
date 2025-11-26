# 🔍 Observabilidade

Observabilidade é a <strong>capacidade de um sistema expor o que está acontecendo internamente por meio dos dados que ele próprio gera</strong>, como logs, métricas e rastreamentos.
Ela possibilita uma análise mais proativa e detalhada do ambiente.

À medida que os projetos de TI se tornam mais dinâmicos — com microsserviços, contêineres, escalabilidade horizontal e integração contínua — o ambiente muda constantemente. Isso aumenta a necessidade de compreender o comportamento do sistema de forma mais profunda.

Com um bom nível de observabilidade, é possível:
- Detectar vazamentos de dados com maior eficiência (ajuda a identificar padrões e anomalias).
- Entender como diferentes linguagens de programação se comportam em produção.
- Investigar erros complexos utilizando rastreamentos detalhados.
- Visualizar dependências entre serviços que muitas vezes passam despercebidas.
- Melhorar o desempenho com base em dados reais, e não apenas em alertas pré-configurados.

### Dados utilizados pela observabilidade

As principais fontes de telemetria:
- logs: registros textuais de eventos, ações e erros;
- Métricas: valores numéricos agregados ao longo do tempo (latência, taxa de erros, uso de CPU/memória).
- Traces (rastreamentos): seguimento de requisições distribuídas entre serviços para correlacionar eventos.

>Telemetria: processo de coletar, registrar e transmitir dados automaticamente de um sistema, dispositivo ou aplicação para um servidor ou ferramenta de monitoramento, permitindo análise, diagnóstico e tomada de decisão à distância.

# 📡 Monitoramento

Monitoramento é o <strong>processo de acompanhar continuamente o estado, o desempenho e a disponibilidade de um sistema</strong>, utilizando métricas, alertas e verificações automatizadas.
Seu objetivo principal é identificar comportamentos inesperados ou degradações antes que afetem usuários ou serviços críticos.

Ao contrário da observabilidade — que busca entender por que algo aconteceu — o monitoramento está focado em <strong>detectar que algo está errado</strong> o mais rápido possível.

Um bom sistema de monitoramento permite:
- Acompanhar a saúde de servidores, aplicações e serviços.
- Detectar quedas, lentidões ou picos anormais de uso.
- Receber alertas automáticos quando métricas ultrapassam limites definidos.
- Identificar gargalos como alto uso de CPU, memória ou I/O (Input/Output).
- Antecipar falhas por meio de tendências históricas.

### Principais dados acompanhados

Entre os principais dados acompanhados estão:
- Status de serviços: verificações de disponibilidade (healthchecks).
- Métricas de desempenho: CPU, memória, disco, rede, latência e throughput.
- Alertas: regras pré-definidas que acionam notificações ao detectar anomalias.
- Logs críticos: mensagens que evidenciam erros ou falhas imediatas.

Enquanto o monitoramento é essencial para detecção rápida, a observabilidade complementa oferecendo entendimento profundo das causas.
Juntos, formam a base para operação eficiente e confiável de sistemas modernos.


<br><br>
<h3>Referências Utilizadas na Construção deste Material:</h3>
https://www.redhat.com/pt-br/topics/devops/what-is-observability
https://www.locaweb.com.br/blog/temas/codigo-aberto/o-que-e-observabilidade-e-monitoramento/
https://www.opservices.com.br/telemetria/
https://aws.amazon.com/pt/compare/the-difference-between-monitoring-and-observability/#:~:text=Com%20os%20sistemas%20de%20monitoramento,centenas%20de%20componentes%20do%20servi%C3%A7o.
