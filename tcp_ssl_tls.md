# 🔗 Segurança e Conexões em Rede

Na internet, proteger os dados em trânsito é essencial para evitar interceptações, vazamentos e ataques. Protocolos como TCP, SSL e TLS são responsáveis por criar conexões confiáveis e seguras entre clientes e servidores, garantindo que informações sensíveis, como senhas e dados pessoais, sejam transmitidas corretamente e de forma protegida. <br>
Este documento apresenta de forma clara a diferença entre TCP, SSL e TLS, destacando seu papel na comunicação e na segurança das aplicações web.

## 🖧 TCP (Transmission Control Protocol – Protocolo de Controle de Transmissão)

O TCP é responsável por garantir que os dados enviados entre dois dispositivos cheguem corretamente e na ordem certa. <br>
Principais características:

- Divide os dados em pacotes e garante que todos cheguem ao destino.
- Reordena pacotes recebidos fora de sequência.
- Detecta erros e solicita retransmissão de pacotes, se necessário.
- Serve como base para protocolos de camada superior, como HTTP e HTTPS.
- Portas comuns: qualquer número entre 0 e 65535.<br>
  Algumas portas conhecidas: <br>
   - 80 → HTTP
   - 443 → HTTPS

## 🔒 SSL (Secure Sockets Layer – Camada de Sockets Segura)

O SSL é um protocolo antigo que cria uma conexão segura e criptografada entre dois dispositivos, como um navegador e um servidor.
Pontos importantes:

- Protege os dados durante o envio, evitando interceptações.
- ⚠️ Foi descontinuado devido a vulnerabilidades de segurança conhecidas.
- Seu uso não é recomendado; todo site moderno deve usar TLS.
- Foi amplamente utilizado no passado para proteger sites via HTTPS.
- Portas associadas historicamente:
   - 443 → HTTPS (SSL/TLS sobre HTTP)
   - 465 → SMTP sobre SSL (envio de e-mails)
   - 993 → IMAP sobre SSL (recebimento de e-mails)

## 🔐 TLS (Transport Layer Security – Segurança da Camada de Transporte)

O TLS é o sucessor do SSL, oferecendo mais segurança e confiabilidade.
Principais pontos:

- Cria conexão criptografada entre cliente e servidor, corrigindo vulnerabilidades do SSL.
- É o padrão atual para conexões seguras na internet, incluindo HTTPS, e-mails e outros serviços.
- Portas padrão:
    - 443 → HTTPS (TLS sobre HTTP)
    - 587 → SMTP com STARTTLS (envio de e-mails)
    - 993 → IMAP sobre TLS (recebimento de e-mails)
      
> Nota:<br>
> SMTP (Simple Mail Transfer Protocol) – Protocolo utilizado para envio de e-mails entre servidores ou de um cliente para o servidor. <br><br>
> IMAP (Internet Message Access Protocol) – Protocolo utilizado para receber e gerenciar e-mails diretamente no servidor, permitindo sincronização entre múltiplos dispositivos. <br><br>

<br><br>
<h3>📚 Referências Utilizadas na Construção deste Material:</h3>
https://www.ssldragon.com/pt/blog/que-e-porta-ssl/ <br>
https://www.digicert.com/pt/what-is-ssl-tls-and-https
