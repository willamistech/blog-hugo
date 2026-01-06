---
title: "Server not found: Saiba como resolver servidor não encontrado no firefox"
date: 2023-07-18
draft: false

cover:
 image: "capa.jpg"
 alt: "Imagem de destaque do post"
 relative: true
---

O arquivo "resolv.conf" é essencial na configuração do sistema Linux para a resolução de nomes de domínio em endereços IP. A resolução de DNS é um processo crucial que permite que os computadores encontrem e se conectem aos servidores apropriados quando você digita um nome de domínio em um navegador ou usa outros serviços de rede.

O que é o arquivo resolv.conf?
O "resolv.conf" é um arquivo de configuração de texto presente em sistemas Linux que contém as informações sobre os servidores de nomes de domínio (DNS) que o sistema deve consultar para resolver os nomes de domínio em endereços IP. Quando um aplicativo no sistema precisa traduzir um nome de domínio em um endereço IP, ele consulta as informações contidas no "resolv.conf" para descobrir quais servidores DNS devem ser usados.

Como alterar o DNS?
Vou utilizar o DNS do google de preferencia mas se quiser pode usar o do seu provedor ou até mesmo da cloudflare que está bem popular por ser mais rápido do que o google. Aqui estão os passos para alterar o arquivo "resolv.conf" e configurá-lo para usar os servidores DNS do Google:

Abra o terminal:
Para fazer alterações no arquivo "resolv.conf", primeiro, precisamos abrir um terminal no Linux. O terminal é uma interface de linha de comandos onde podemos executar comandos no sistema.

Verifique as permissões:
Antes de editar o arquivo "resolv.conf", certifique-se de que você tenha as permissões necessárias para alterá-lo. Isso geralmente requer privilégios de superusuário (root). Para obter esses privilégios, digite o seguinte comando no terminal e insira a senha de administrador quando solicitado:
```bash
sudo su
```
Abra o arquivo "resolv.conf" em um editor de texto:
A seguir, vamos abrir o arquivo "resolv.conf" em um editor de texto. O editor de texto "nano" é uma opção simples e amplamente disponível. Digite o seguinte comando para abrir o arquivo:
```bash
nano /etc/resolv.conf
```
Edite o arquivo "resolv.conf":
O arquivo "resolv.conf" é um arquivo de texto simples. Nesta etapa, você verá as configurações atuais de DNS. Se houver algum conteúdo presente, mude o endereço de 127.0.0.53 para 8.8.8.8. Veja o exemplo:
```bash
nameserver 8.8.8.8
```
Para salvar as alterações no "resolv.conf" usando o editor "nano", pressione as teclas "Ctrl + O" e, em seguida, pressione "Enter" para confirmar o nome do arquivo. Para sair do editor, pressione "Ctrl + X".

Reinicie o serviço de rede (opcional):
Algumas distribuições Linux podem exigir que você reinicie o serviço de rede para que as alterações entrem em vigor. Para fazer isso, execute o seguinte comando:

sudo systemctl restart networking

Agora basta acessar qualquer site no seu navegador, espero ter ajudado deixe seu comentário e compartilhe nosso conteúdo.