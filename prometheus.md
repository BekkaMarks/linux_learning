# 🔥 Introdução ao Prometheus

Prometheus é uma ferramenta de monitoramento que coleta métricas em tempo real de serviços e sistemas, armazena os dados em um banco de séries temporais e permite criar alertas e dashboards para acompanhar o desempenho da infraestrutura.

### Características:

- Modelo multi-dimensional
> Funciona permitindo que cada métrica tenha labels (rótulos) que adicionam contexto e permitem consultas mais detalhadas e flexíveis.
> Introdução ao Prometheus

- Independência entre servidores
> Prometheus não depende de armazenamento distribuído; cada instância opera de forma isolada, o que simplifica a arquitetura e evita acoplamentos complexos.

- Modelo HTTP pull para coleta
> O Prometheus coleta métricas buscando periodicamente informações nos alvos (targets) através do protocolo HTTP — um fluxo baseado em pull, onde o próprio servidor inicia a coleta.

- Envio de métricas via gateway para trabalhos em lote
> Para cenários em que não é possível expor um endpoint contínuo (como scripts de curta duração ou jobs em lote), o Prometheus suporta o envio de séries temporais por meio do Pushgateway, um componente intermediário.

- Descoberta de alvos
> As aplicações monitoradas podem ser encontradas por:<br>
> - descoberta de serviço (como Kubernetes, Consul, EC2), ou<br>
> - configuração estática, definida diretamente no arquivo prometheus.yml.

- Suporte a gráficos e painéis
> Embora o Prometheus possua uma interface básica para consultas, ele se integra facilmente a ferramentas como Grafana para visualizações mais avançadas.

- Federação hierárquica e horizontal
> O Prometheus permite que uma instância consulte métricas de outras instâncias, criando uma federação. Isso facilita:<br>
> - consolidação de métricas entre ambientes;<br>
> - escalabilidade horizontal;<br>
> - agrupamento de dados provenientes de diferentes regiões ou clusters.

- Linguagem própria (PromQL) para queries de dados em formato <i>time series</i>
> Time series (série temporal) é um conjunto de valores registrados ao longo do tempo, cada ponto contendo:<br>
>  - um instante (timestamp);<br>
>  - um valor numérico;<br>
>  - (no Prometheus) um conjunto de labels;<br>
> Exemplo: quantidade de requisições HTTP por segundo — registrada a cada 5 segundos.

### 🛠️ Como o Prometheus Coleta, Armazena e Alerta

1. Ciclo de coleta (Scrape Cycle)<br>
O Prometheus funciona realizando ciclos periódicos de coleta. A cada intervalo configurado (por exemplo, 15 segundos), ele lê a lista de alvos definida no prometheus.yml, acessa o endpoint /metrics de cada serviço e captura os valores expostos. Esses dados são convertidos em séries temporais e armazenados automaticamente.

2. Armazenamento interno (TSDB)<br>
O Prometheus salva todas as métricas no seu banco de séries temporais embutido (TSDB). O armazenamento é feito em blocos organizados por intervalos de tempo, combinando memória, arquivos WAL (Write-Ahead Log) e compactação automática para otimizar desempenho e espaço em disco.

3. Sistema de Alertas (Alertmanager)<br>
O Prometheus avalia constantemente regras de alerta definidas pelos usuários. Quando uma condição é atendida (ex.: uso de CPU acima de 80% por 5 minutos), o Prometheus dispara um alerta para o Alertmanager, que é responsável por agrupar, silenciar e encaminhar notificações para canais como Slack, e-mail, Telegram ou sistemas de incidentes.


<br><br>
<h3>🔗 Referências Utilizadas na Construção deste Material:</h3>
https://github.com/prometheus/prometheus
https://medium.com/techbloghotmart/o-que-s%C3%A3o-s%C3%A9ries-temporais-e-como-aplicar-em-machine-learning-6ea5d94bec78
https://blog.4linux.com.br/primeiros-passos-com-promql/
https://medium.com/@habbema/introdu%C3%A7%C3%A3o-ao-prometheus-8ae1cd56ca97
