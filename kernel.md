# 🧠 Kernel: o Núcleo do Sistema Operacional

O kernel é o núcleo do sistema operacional. Ele é responsável por gerenciar informações, processos e todo o funcionamento interno do computador.
Assim que o dispositivo é ligado, o kernel é inicializado e passa a reconhecer, controlar e otimizar o uso dos componentes físicos — como memória, processador, armazenamento e dispositivos externos.

Em outras palavras:

<strong><em>O kernel conecta o hardware (parte física) ao software (parte lógica), permitindo que tudo funcione em harmonia.</em><strong>

## Principais funções do Kernel
### 1. Gerenciamento de Memória
O kernel decide onde cada informação será armazenada na memória após ser lida.
Ele controla o uso da memória, evita sobrecargas e até alerta quando o sistema está ficando sem espaço.
É ele que organiza, realoca e protege as áreas de memória usadas por cada programa.

---

### 2. Gerenciamento de Processos
O kernel determina quais tarefas devem ser executadas primeiro pelo processador.
Ele organiza a fila de processos, dá prioridade ao que é mais importante e garante que tudo seja processado sem travamentos.

---

### 3. Gerenciamento de Dispositivos
Todo dispositivo conectado — como mouse, teclado, pen-drive, placa de vídeo ou impressora — precisa passar pelo kernel.
Ele identifica, valida e prepara esses dispositivos para uso, permitindo que o sistema operacional se comunique com eles.

---

### 4. Chamadas de Sistema (System Calls)
Quando um programa precisa fazer algo importante (como ler um arquivo, escrever no disco ou usar a rede), ele faz uma chamada de sistema.
O kernel analisa a solicitação, decide se é permitida e executa a ação necessária.
Sem isso, nenhum programa poderia interagir com o hardware.

           Applications
                ⬍
              Kernel
      ⬍        ⬍        ⬍
     CPU     Memory   Devices
     
<br><br>
<h3>Referências Utilizadas na Construção deste Material:</h3>
https://www.corsair.com/pt/pt/explorer/glossary/what-is-a-kernel/#:~:text=O%20kernel%20%C3%A9%20o%20n%C3%BAcleo%20de%20um,que%20mant%C3%A9m%20tudo%20a%20funcionar%20sem%20colis%C3%B5es. <br>
https://www.certificacaolinux.com.br/como-funciona-o-kernel-do-linux/ <br>
https://www.redhat.com/pt-br/topics/linux/what-is-the-linux-kernel
