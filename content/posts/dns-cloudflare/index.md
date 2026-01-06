---
title: "Por que escolhi DNS Cloudflare em vez de blacklist e proxy no meu ambiente"
date: 2026-01-05
draft: false
categories: ["Redes"]

cover:
 image: "capa.jpg"
 alt: "Imagem de destaque do post"
 relative: true
---

Recentemente optei por aplicar DNS com filtragem de conteúdo no pfSense, como alternativa a blocklists e proxies mais complexos. No meu cenário, optei pelo uso de DNS Cloudflare com proteção (1.1.1.3) integrado ao pfSense, e o resultado foi muito mais eficiente do que soluções baseadas em blacklist ou proxy.

## Por que o DNS Cloudflare funcionou melhor

### Simplicidade operacional:

Não exige proxy transparente
Não interfere no tráfego HTTPS
Fácil de manter e documentar

### Estabilidade:

Não impacta sistemas críticos
Reduz falhas intermitentes comuns em proxies
Menos pontos de quebra na rede

### Segurança eficiente:

Bloqueio de conteúdo adulto
Proteção contra malware e phishing
Filtragem aplicada no nível correto: resolução de nomes

### Desempenho:

Baixa latência
Respostas rápidas
Experiência de navegação fluida

## Por que blacklist e proxy não eram ideais

Maior complexidade de configuração
Manutenção constante de listas
Impacto em HTTPS
Risco de afetar TEF, bancos e sistemas fiscais

Para o meu ambiente, o custo operacional dessas soluções era maior do que o benefício entregue. Nem sempre a solução mais robusta é a mais adequada. No meu cenário, o DNS Cloudflare ofereceu o melhor equilíbrio entre segurança, simplicidade e estabilidade, atendendo perfeitamente às necessidades da empresa sem comprometer a operação.