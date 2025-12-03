
<h1>⚙️ Serviços no Linux</h1> 

<p>No Linux, um serviço é um <strong><i>programa executado em segundo plano</i></strong>, geralmente iniciado automaticamente quando o sistema é ligado. Esses serviços são controlados pelo <strong>systemd</strong>, usado como padrão na maior parte das distribuições modernas (Ubuntu, Debian, CentOS, Fedora, entre outras).</p> 

<h2>O que é um init system</h2> 

<p>O <strong>init system</strong> (sistema de inicialização) é o componente responsável por iniciar todo o sistema operacional. Assim que o computador liga e o kernel do Linux é carregado, o init system é o primeiro processo iniciado — e a partir dele todo o restante do sistema começa a funcionar.</p> 

<h2> O papel do systemd</h2> 

<p>O <strong>systemd</strong> é o init system padrão da maioria das distribuições modernas. Ele assume a responsabilidade de iniciar e gerenciar todos os serviços essenciais do sistema, organizando esses processos em etapas e garantindo que tudo suba na ordem correta.</p> 

<p>Assim que o kernel é ativado, o systemd entra em ação para:</p> 
<ul> 
  <li>inicializar serviços essenciais do sistema;</li> 
  <li>preparar o ambiente de hardware, como placa de vídeo e processador;</li>
  <li>gerenciar processos de maneira padronizada e eficiente;</li> 
  <li>controlar serviços em execução, permitindo iniciar, parar, reiniciar e monitorar cada um deles.
  </li> 
</ul> 

<h2> Unidades (Units)</h2> 

<p>O systemd organiza suas tarefas em componentes chamados <strong>unidades (units)</strong>. Cada unit representa um tipo específico de recurso, como serviços, sockets, dispositivos, pontos de montagem e muito mais.</p>

<p>Alguns tipos comuns de units:</p> <ul> <li><strong>service</strong>: define um serviço em execução;</li> <li><strong>socket</strong>: gerencia comunicação baseada em sockets;</li> <li><strong>mount</strong>: define pontos de montagem do sistema de arquivos;</li> <li><strong>timer</strong>: substitui tarefas cron, agendando execuções.</li> </ul> <p>Em resumo, o systemd funciona como um <strong>gerenciador completo de sistemas e serviços</strong>, responsável por garantir que o Linux inicialize corretamente e mantenha os serviços funcionando de forma estável.</p>
