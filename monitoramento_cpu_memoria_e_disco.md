# Monitoramento de CPU, Memória e Espaço em Disco
O monitoramento de CPU, memória e espaço em disco é fundamental para assegurar a estabilidade e a eficiência de sistemas Linux. Monitorar esses recursos permite detectar sobrecargas, antecipar possíveis falhas, evitar a indisponibilidade de serviços e preservar o desempenho. Por meio de comandos nativos ou ferramentas especializadas, é possível acompanhar o uso em tempo real, identificar gargalos e tomar medidas preventivas antes que ocorram impactos no ambiente.

Abaixo seguem comandos que auxiliam a visualização de cada etapa dos monitoramentos mencionados nesse guia.

### <i>Verificação da utilização da CPU</i>

### ➜ <strong>top</strong>
Utilitário que exibe informações sobre os processos que estão sendo executados em tempo real juntamente com utilização da CPU, memória e outras métricas. 

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
Exibe o uso da CPU por núcleo, mostrando como cada parte da CPU está sendo utilizada (processos de usuário, kernel, espera por disco e tempo ocioso). Ajuda a identificar se algum núcleo está sobrecarregado ou se há gargalos de desempenho.

```bash
sudo apt-get install sysstat   # Em distribuições baseadas em Debian/Ubuntu
sudo yum install sysstat       # Em distribuições baseadas em Red Hat/Fedora
mpstat -P ALL
```

### <i>Verificação de Espaço em Disco</i>

### ➜ <strong>df</strong>
O comando def (disk free) exibe a quantidade de espaço disponível e utilizado em todas as partições montadas no sistema.

```bash
df -h
```
A opção `-h` torna a saída légivel, exibindo os tamanhos em unidades compreensíveis (MB e GB).

### ➜ <strong>du</strong>
Diferente do comando df, o comando du (disk usage) permite examinar o uso de espaço em diretórios específicos.

```bash
du -sh /caminho/ára/diretorio
```
A opção -s resume o uso do diretório, enquanto o -h exibe o tamanho em um formato legível.

### ➜ <strong>ncdu</strong>
Possibilita uma visualização mais interativa e detalhada do uso de espaço no disco.

```bash
sudo apt-get install ncdu   # Em distribuições baseadas em Debian/Ubuntu
sudo yum install ncdu       # Em distribuições baseadas em Red Hat/Fedora
ncdu /
```
### <i>Verificação de Memória RAM</i>

### ➜ <strong>free</strong>
Exibe a quantidade de memória física e swap disponível e utilizado no sistema.

```bash
free -h
```
> Memória SWAP é uma área do disco usada como extensão da RAM quando a memória física acaba.

### ➜ <strong>vmstat</strong>
O comando vmstat (Virtual Memory Statistics) fornece uma visão mais detalhada do uso da memória, juntamente com informações sobre processos, CPU, swap, I/O, e mais.

```bash
vmstat 5
```
Neste exemplo, o vmstat irá atualizar as estatísticas a cada 5 segundos, oferecendo uma visão contínua do estado do sistema.

### ➜ <strong>smem</strong>
Ele exibe a quantidade de memória usada, incluindo a memória compartilhada.

```bash
sudo apt-get install smem   # Em distribuições baseadas em Debian/Ubuntu
smem
```

### <i>Verificação de Uptime do Sistema</i>
Exibe há quanto tempo o sistema está ativo, número de usuários logados e a carga média do sistema.

```bash
uptime
```

<br><br>
<h3>Referências Utilizadas na Construção deste Material:</h3>
https://nerdexpert.com.br/monitoramento-de-cpu-memoria-e-espaco-em-disco-no-linux-comandos-essenciais/
https://diolinux.com.br/tutoriais/o-que-e-memoria-swap.html
https://www.vivaolinux.com.br/dica/Usando-o-NcDU-(Ncurses-Disk-Usage)
https://centric.com.br/blog/6-metricas-de-desempenho-do-servidor-linux-a-serem-observadas/?__cf_chl_tk=dAsSSxGxqFwqNEZnTKC7DXVb5UuFevubGJkQ1nMvJfY-1764178867-1.0.1.1-MjhlqETVx_cH4D2ASoX9.iFvaJ7UuHf5PPkQ86ww9Dk
