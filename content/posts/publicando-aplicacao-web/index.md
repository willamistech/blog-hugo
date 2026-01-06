---
title: "Publicando uma aplicação GlassFish com Nginx, HTTPS e pfSense"
date: 2026-01-04
draft: false

cover:
 image: "capa.jpg"
 alt: "Imagem de destaque do post"
 relative: true
---

Em ambientes reais, principalmente quando lidamos com sistemas em produção, publicar uma aplicação web não se resume a expor uma porta no firewall.
Esse tipo de abordagem simplista gera riscos de segurança, instabilidade e dificuldade de manutenção a médio e longo prazo.

Problemas desse cenário:

Sem HTTPS
Porta exposta
IP exposto
Inseguro para fornecedores externos
Difícil de manter e documentar

O objetivo era publicar o sistema Cotação Web para fornecedores externos, que originalmente rodava na porta 34001, garantido:

Segura
Profissionalismo
Padronização
Não expor IP nem porta

A aplicação rodava sobre Java (GlassFish), no módulo web do ERP.

## Soluções implementadas

### Configuração de DNS no hPanel

O domínio já estava registrado no Registro.br e usando DNS da Hostinger. Criamos o registro no gerenciador DNS:

```bash
Tipo: A
Nome: contexto
Aponta para: IP público da empresa
TTL: 300
```

### Firewall e NAT

Criei as regras de NAT Port Forward:

```bash
WAN TCP 80 → 192.168.50.235:80

WAN TCP 443 → 192.168.50.235:443
```

Assim, apenas as portas padrão web ficam expostas externamente.

### Nginx como proxy reverso

Nginx foi utilizado como proxy reverso, protegendo o GlassFish

Instalação no servidor Linux (Xubuntu):

```bash
sudo apt update

sudo apt install nginx -y

systemctl status nginx

sudo nano /etc/nginx/sites-available/contexto

Configuração inicial:

server {
server_name contexto.empresa.com.br;

location / {
proxy_pass http://127.0.0.1:34001;
proxy_set_header Host $host;
proxy_set_header X-Real-IP $remote_addr;
proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
proxy_set_header X-Forwarded-Proto $scheme;
}
}
```

Ativei o site:

```bash
sudo ln -s /etc/nginx/sites-available/contexto /etc/nginx/sites-enabled/
```

E desativei o site default (fundamental):

```bash
sudo rm /etc/nginx/sites-enabled/default
```

### Certificado SSL – Let’s Encrypt

O HTTPS foi implementado com Let’s Encrypt, garantindo criptografia e confiança.

Instalação:

```bash
sudo apt install certbot python3-certbot-nginx -y
```

Geração do certificado:

```bash
sudo certbot --nginx -d contexto.empresa.com.br
```

Durante o processo:

Informei e-mail válido
Aceitei os termos
Confirmei o redirecionamento HTTP → HTTPS

Resultado:

```bash
Congratulations! You have successfully enabled HTTPS
```

Entendimento da aplicação

O Cotação Web não rodava na raiz /. O caminho correto da aplicação é:

/php/contexto/login.php

Por isso:

https://contexto.empresa.com.br não funcionava sozinho
https://contexto.empresa.com.br/php/contexto/login.php funcionava

Embelezando a URL

Ajustei o Nginx para redirecionar automaticamente a raiz:

```bash
location = / {
return 302 /php/cotexto/login.php;
}

Configuração final do site (resumo):

server {
server_name contexto.empresa.com.br;

location = / {
return 302 /php/contexto/login.php;
}

location / {
proxy_pass http://127.0.0.1:34001;
proxy_set_header Host $host;
proxy_set_header X-Real-IP $remote_addr;
proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
proxy_set_header X-Forwarded-Proto https;
proxy_set_header X-Forwarded-Port 443;
}

listen 443 ssl;
}
```

Aplicação:

```bash
sudo nginx -t
sudo systemctl reload nginx
```

Resultado final

Agora, ao acessar:

https://contexto.empresa.com.br

O usuário é automaticamente redirecionado para o login do sistema, com:

🔒 HTTPS válido
🌐 Domínio profissional
❌ Sem IP exposto
❌ Sem porta exposta
🧱 GlassFish protegido atrás do Nginx.