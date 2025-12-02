# 🌐 NGINX: Servidor Web, Cache e Proxy Reverso

O NGINX é um servidor web de alta performance responsável por lidar com requisições HTTP. Ele atua ouvindo uma porta e pode realizar diferentes funções ao receber uma requisição:

- Retornar conteúdo estático (imagens, CSS, JS, arquivos);
- Redirecionar a requisição para o servidor responsável pela aplicação;
- Entregar uma resposta cacheada, evitando que a requisição chegue novamente ao servidor final;
- Servir como ponto de entrada em uma arquitetura de microserviços.

### Modelo de funcionamento

Diferente de servidores que criam um processo dedicado para cada requisição, o NGINX trabalha com um modelo baseado em um processo principal (“master process”), que cria workers conforme a quantidade de núcleos de CPU.
Cada worker opera de forma concorrente, gerenciando múltiplas conexões.<br>
  Diferença:<br>
            - <strong>Paralelo:</strong> tarefas realmente executadas ao mesmo tempo (múltiplos núcleos).<br>
            - <strong>Concorrente:</strong> o worker alterna rapidamente entre tarefas, dando a sensação de execução simultânea.
  
Esse modelo permite que o NGINX atenda milhares de conexões com baixo consumo de recursos.

### Proxy Comum

Um proxy comum atua entre os computadores de uma rede interna e a internet. Todas as requisições que saem da intranet passam primeiro por esse proxy.<br>
Funções típicas:
- Filtrar e bloquear acessos a sites não permitidos (ex.: tentar acessar a Netflix no computador da empresa e ser bloqueado).
- Registrar logs de acesso;
- Aplicar políticas de controle;
- Fazer cache em memória ou disco para acelerar requisições repetidas.<br>
Ele funciona como um middleman, intermediando as conexões.

### Proxy Reverso

O proxy reverso atua na frente dos servidores, recebendo as requisições antes delas chegarem às aplicações internas. Ele:
- distribui carga entre servidores (load balancing);
- melhora a segurança escondendo a infraestrutura interna;
- serve conteúdo estático ou cacheado;
- encaminha a requisição ao serviço correto.

O NGINX é muito usado como proxy reverso exatamente por ser leve, rápido e eficiente no gerenciamento de múltiplas conexões.

<br><br>
<h3>Referências Utilizadas na Construção deste Material:</h3>
https://www.youtube.com/watch?v=gd_cUmwzgEM&t=2925s
