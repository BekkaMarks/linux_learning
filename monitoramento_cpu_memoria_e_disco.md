# Monitoramento de CPU, Memória e Espaço em Disco
O monitoramento de CPU, memória e espaço em disco é fundamental para assegurar a estabilidade e a eficiência de sistemas Linux. Monitorar esses recursos permite detectar sobrecargas, antecipar possíveis falhas, evitar a indisponibilidade de serviços e preservar o desempenho. Por meio de comandos nativos ou ferramentas especializadas, é possível acompanhar o uso em tempo real, identificar gargalos e tomar medidas preventivas antes que ocorram impactos no ambiente.

Abaixo segue comandos que auxiliam a visualização de cada etapa dos monitoramentos mencionados nesse guia.

### <i>Varificação da Utilização da CPU</i>

### ➜ <strong>top</strong>
Utilitário que exibe informações sobre os processos que estão sendo executados em tempo real juntamente com utilização da CPU memória e outras métricas. 
```bash
top
```

### ➜ <strong>htop</strong>
Versão mais avançada do top. O htop também exibe informações de uso da CPU em tempo real, mas com a vantagem de oferecer uma interface mais interativa, colorida e intuitiva, facilitando a visualização de processos e recursos do sistema.

Para instalar o htop, utilize o comando correspondente à sua distribuição:

```bash
sudo apt-get install htop   # Em distribuições baseadas em Debian/Ubuntu
sudo yum install htop       # Em distribuições baseadas em Red Hat/Fedora
htop
```
### ➜ <strong>mpstat</strong>


















<br><br>
<h3>Referências Utilizadas na Construção deste Material:</h3>
https://nerdexpert.com.br/monitoramento-de-cpu-memoria-e-espaco-em-disco-no-linux-comandos-essenciais/
