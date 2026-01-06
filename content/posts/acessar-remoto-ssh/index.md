---
title: "Como acessar remotamente outro computador via SSH"
date: 2023-07-08
draft: false

cover:
 image: "capa.jpg"
 alt: "Imagem de destaque do post"
 relative: true
---

No mundo conectado de hoje, onde a colaboração e o trabalho remoto são cada vez mais comuns, a capacidade de acessar outro computador de forma segura e eficiente é essencial. O SSH (Secure Shell) é uma ferramenta poderosa que permite o acesso remoto a computadores e servidores de maneira segura. Veja como acessar outro computador por meio do SSH e desfrutar dos benefícios da conexão remota.

O que é SSH e como funciona?
O SSH é um protocolo de rede que permite a comunicação segura entre dois computadores por meio de uma conexão criptografada. Ele oferece uma maneira de acessar um computador remoto, executar comandos e transferir arquivos de forma segura. O SSH utiliza uma combinação de criptografia assimétrica e simétrica para garantir a privacidade e a integridade dos dados transmitidos. Vamos explorar como utilizar o SSH para acessar remotamente outro computador.

1.  Verifique se o computador de destino possui o SSH habilitado:
Antes de estabelecer uma conexão SSH, certifique-se de que o computador que você deseja acessar tenha o servidor SSH instalado e ativado. 
```bash
service ssh status
```
Em sistemas baseados em Linux, como Ubuntu ou CentOS, o SSH geralmente já está instalado por padrão. Caso contrário, você precisará instalar e configurar o servidor SSH no computador de destino.

2. Instalando o SSH no Servidor ou no seu computador:
```bash
apt install openssh-server
```
3. Instalando o SSH no cliente ou no computador de destino:
```bash
apt install openssh-client
```
4. Conheça o endereço IP do computador de destino:
Você precisará saber o endereço IP do computador que deseja acessar. Isso pode ser obtido de várias maneiras, como perguntar ao administrador do sistema ou usando comandos como "ipconfig" no Windows ou "ip addr" no Linux.
```bash
ip addr
```
5. Estabeleça a conexão SSH a partir do seu computador:
Agora, abra um terminal ou prompt de comando no seu computador e digite o seguinte comando para estabelecer a conexão SSH:
```bash
ssh nome-de-usuário@endereço-IP-do-computador
```
Por exemplo, se o nome de usuário for "willamis" e o endereço IP for "192.168.0.100", o comando ficará assim:
```bash
ssh willamis@192.168.0.100
```
6. Autentique-se e acesse o computador remoto:
Após executar o comando SSH, você será solicitado para confirmar o acesso, depois a digitar a senha do usuário no computador de destino. Digite a senha correta e pressione Enter. Se as credenciais estiverem corretas, você terá acesso ao computador remoto e poderá executar comandos como se estivesse fisicamente presente nele.

O SSH é uma ferramenta essencial para acessar computadores remotamente de forma segura. Com alguns passos simples, você pode estabelecer uma conexão SSH e desfrutar dos benefícios do acesso remoto. Lembre-se de tomar medidas adequadas de segurança, como usar senhas fortes e manter o software atualizado, para garantir a integridade e a confidencialidade dos dados durante a conexão SSH. Experimente essa tecnologia e amplie suas possibilidades de colaboração e gerenciamento remoto!