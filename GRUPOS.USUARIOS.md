<h1>Grupos e Usuários (Linux)</h1>

<p>No Linux, um usuário (user) é uma conta que representa uma pessoa, serviço ou processo dentro do sistema. Cada usuário possui um identificador numérico único (UID), um diretório pessoal, um shell padrão e um conjunto específico de permissões. Essa estrutura organiza e separa as atividades de cada conta, tornando o sistema mais seguro e fácil de administrar, pois limita o acesso apenas ao que foi permitido.</p>

<p>A existência de vários usuários é especialmente útil em ambientes onde várias pessoas utilizam o mesmo computador ou servidor. Em empresas, cada funcionário pode acessar recursos compartilhados sem interferir nos arquivos dos colegas. Em escolas, contas separadas garantem a privacidade de materiais, notas e atividades de alunos e professores. Em servidores, equipes como desenvolvimento, banco de dados e suporte trabalham com permissões específicas, evitando acessos indevidos.</p>

<p>Uma forma simples de visualizar isso é imaginar o computador como uma casa: você é o administrador, responsável por todas as portas, mas pode permitir que outras pessoas entrem apenas nos cômodos necessários. No Linux funciona da mesma forma — cada usuário tem seu próprio espaço protegido, e o administrador decide o que pode ser acessado ou não. Essa organização traz privacidade, controle e segurança para qualquer ambiente.</p>

<h3>As informações do usuário são armazenadas em:</h3>

<table>
    <tbody>
        <tr>
          <td>/etc/passwd</td>
          <td>Detalhes básicos da conta.</td>
        </tr>
         <tr>
            <td>/etc/shadow</td>
            <td>Senhas criptografadas.</td>
        </tr>
          <tr>
            <td>/etc/group</td>
            <td>Informações sobre associação a grupos.</td>
          </tr>
    </tbody>
</table>

<p>Quando um usuário executa um comando, acessa um arquivo ou realiza tarefas administrativas, o Linux verifica esses arquivos para decidir se permite ou nega a ação.</p>

<h2>Tipos de Usuário</h2>

<form>
    <ol>
        <li>
            <strong>Root</strong>:
            <ul>
                <li>
                   O usuário root (UID 0) tem permissão de executar <strong>qualquer ação</strong>, incluíndo: Instalar ou remover software, alterar arquivos do sistema, editar os dados de qualquer usuário, reiniciar servições do sistetam, etc. <strong>O acesso root deve ser tratado com cuidado, pois um único erro pode comprometer o sistema</strong>.<br><br>
                </li>
            </ul>
        </li>
        <li>
            <strong>Regular</strong>
            <ul>
              <li>
                São criadas para funionários, desenvolvedores, equipes de suporte ou qualquer pessoa que precise de acesso controlado. Essas contas possuem seu próprio diretório pessoal, podem armazenar arquivos, executar apliativos pemitidos e não é possível realizar modificações e configurações do sistema. <strong>Suas ações são limitadas por questões de segurança</strong>.<br><br>
              </li>
          </ul>
        </li>
       <li>
          <strong>Usuários do sistema</strong>:
        <ul>
          <li>
             Esses usuários não se destinam ao login. Eles são criados por serviços e aplicativos para executar processos com segurança. Por exemplo: MySQL para bancos de dados, www-dados para servidores web, daemon para tarefas em segundo plano.<br><br>
            </li>
          </ul>
        </li>
    </ol>
</form>

<h2>Criando Usuários</h2>

<p>Formas comuns de se criar usuários no Linux:</p>

<table>
    <tbody>
        <tr>
          <td><code><strong>useradd name</strong></code></td>
          <td>Ferramenta de linha de comando básico e direto para adicionar novos usuários ao sistema, mas não fornece uma interface interativa e amigável durante o processo.</td>
        </tr>
    </tbody>
</table>
<form>
    <ol>
         <ul>
             <li>
            ⚠️ Para o comando useradd, lembre-se de criar uma senha <strong>'sudo passwd name'</strong>, a home <strong>'sudo mkdir /home/name'</strong> e o grupo <strong>'sudo chown name:name /home/neme'</strong>
          </li>
        </ul>
    </ol>
</form>
<table>
      <tr>
          <td><code><strong>useradd -m name</strong></code></td>
          <td>Cria o usuário e também cria o diretório home (por exemplo /home/name) caso não exista, copiando os arquivos padrão de /etc/skel e ajustando a propriedade/permissões. O comando não define senha automaticamente
          </td>
        </tr>
</table>
<table>
    <tr>
        <td><code><strong>adduser name</strong></code></td>
        <td>Ferramenta amigável e interativa para criar novos usuário ao sistema. Ele apresenta uma série de pergntas durante o processo de criação, como o nome completo do usuário, senha, grupos adicionais , tornando a tarefa mais simples para iniciantes.<br> O adduser também cuida automaticamente de várias configurações padrão, como a criação de uma pasta inicial para o usuário em /home e a atribuição de um shell padrão.
        </td>
    </tr>
</table>
<form>
  <ol>
    <ul>
      <li>
        ⚠️ Importante: os comandos mencionados precisam ser executados com privilégios de administrador (sudo ou root), pois criar, modificar ou remover usuários altera partes críticas do sistema.<br><br>
      </li>
    </ul>
  </ol>
</form>

<h2>Opções de comando</h2>

<table>
  <thead>
        <th>Comando</th>
        <th>Funcionalidade</th>
    </thead>
    <tbody>
        <tr>
          <td>-m</td>
          <td>
              Cria automaticamente o diretório home do usuário. Se o diretório não existir, ele é criado a partir de /etc/skel.
          </td>
        </tr>
         <tr>
            <td>-d</td>
            <td>
                Define manualmente o diretório home do usuário.<br>Ex:<code>useradd -m <strong>-d /opt/erpnext</strong></code>... <br>Normalmente seria /home/erpnext, mas aqui está sendo definido para opt/erpnext. 
            </td>
        </tr>
        <tr>
            <td>-U</td>
            <td>
                Cria um grupo com o mesmo nome do usuário automaticamente.<br>Ex: Usuário: erpnext, Grupo criado: erpnext.<br> Esse grupo será o grupo primário do usuário. 
            </td>
        </tr>
        <tr>
            <td>-u</td>
            <td>
                Define manualmente o UID.
            </td>
        </tr>
          </tr>
        <tr>
            <td>-r</td>
            <td>
                Cria um usuário do sistema (system user).<br>Características: UID geralmente abaixo de 1000 (em muitas distros); Ideal para serviços, daemons e aplicações;Não cria entradas em alguns arquivos como /var/mail.   
            </td>
        </tr>
         <tr>
            <td>-s</td>
            <td>
               Define o shell padrão do usuário.<br>Ex: <code>useradd -m -d /opt/erpnext -U -r <strong>-s /bin/bash</strong> erpnext</code>. Aqui está sendo especificado que o user erpnext deve usar: /bin/bash.
            </td>
        </tr>
          </tr>
    </tbody>
</table>

<h2>Removendo Usuários</h2> 

<p>Existem duas formas comuns de remover contas: <strong>userdel</strong> e <strong>deluser</strong>.</p> 

<p><strong>✔ userdel</strong> é o comando tradicional, disponível em todas as distribuições como parte das ferramentas básicas do sistema. É uma ferramenta de baixo nível que atende às necessidades de remoção de contas, porém exige cuidado e conhecimento técnico ao ser utilizada.</p> 

<table>
    <tbody>
        <tr>
          <td><code>sudo userdel -r teste </code>: Remove a conta "teste" do sistema. Aqui o a opção -r também tenta apagar o diretório home (/home/teste) e o mail spool do usuário (verifique em /var/mail ou /var/spool/mail com:<code>ls -l /var/mail</code> e <code>ls -l /var/spool/mail</code>).</td>
        </tr>
    </tbody>
</table>

<p><strong>deluser</strong> é um utilitário mais amigável (presente, por exemplo, em Debian/Ubuntu) que automatiza etapas e oferece uma abordagem mais segura e prática, semelhante ao comportamento do <strong>adduser</strong> na criação de contas. Em geral, <strong>userdel</strong> é indicado para cenários avançados; <strong>deluser</strong> facilita a rotina do administrador ou do usuário comum.</p> 

<p>Se, ao tentar remover uma conta, ocorrer a mensagem:</p>

<p><strong><i>userdel: user teste is currently used by process 18751</i></strong></p> 

<p>Proceda da seguinte forma (com <strong>sudo</strong> ou como root):</p> 
<ul> 
    <li>Identifique o processo: <code>ps -f -p 18751</code> ou liste todos os processos do usuário: <code>ps -u teste</code> / <code>pgrep -u teste -l</code>.
</li> 
    <li>Tente encerrar a sessão de forma ordenada (se o sistema usar systemd): <code>sudo loginctl terminate-user teste</code>.
</li> 
    <li>Se necessário, encerre o PID específico: <code>sudo kill 18751</code>. Como último recurso, use <code>sudo kill -9 18751</code>, ciente dos riscos de interromper processos abruptamente.
</li> 
    <li>Após confirmar que não há processos ativos do usuário, execute: <code>sudo userdel -r teste</code> ou <code>sudo deluser --remove-home teste</code>.
</li> 
</ul>
    <table> 
        <thead>
            <th>Comando</th> 
            <th>Funcionalidade</th> 
        </thead> 
        <tbody>
            <tr> 
                <td>ps</td> 
            <td> 
                Exibe informações sobre os processos em execução na máquina. 
            </td> 
        </tr> 
            <tr> 
                <td>-f</td> 
            <td> 
                Mostra o processo em formato "full" (informação completa). 
            </td> 
        </tr> 
        <tr> 
            <td>-p</td> 
        <td> Seleciona pelo ID (PID) especificado; requer o argumento do PID, por exemplo <code>-p 18751</code> ou <code>-p18751</code>. 
        </td> 
        </tr> 
            <tr> 
                <td>-u</td> 
                <td> Lista processos do usuário indicado, por exemplo <code>ps -u teste</code>.
                </td> 
            </tr> 
            <tr>
                <td>-fp</td> 
                <td> Combina as opções <code>-f</code> e <code>-p</code>; por exemplo <code>ps -f -p 18751</code> ou <code>ps -fp 18751</code>. Note que o <code>-p</code> exige o PID como argumento. </td>
            </tr> 
        </tbody> 
    </table>
<br><br>
<h3>Referências Utilizadas na Construção deste Material:</h3>
https://dev.to/diogoizele/grupos-e-usuarios-em-linux-o-que-voce-precisa-saber-4lp9<br>
https://blog.scalefusion.com/pt/gerenciamento-de-usu%C3%A1rios-Linux/<br>
https://linuxvisual.com/comando-userdel/<br>
https://life.inf.ufes.br/wiki/como-adicionar-usuario-linux/<br>
https://guialinux.uniriotec.br/comandos-do-linux/<br>
