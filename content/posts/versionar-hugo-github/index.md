---
title: "Como versionar um projeto Hugo no GitHub usando GitHub Desktop (sem dor de cabeça)"
date: 2025-12-24
draft: false

cover:
 image: "capa.jpg"
 alt: "Imagem de destaque do post"
 relative: true
---

Quando começamos a trabalhar com sites estáticos usando Hugo, uma das primeiras dúvidas é como versionar o projeto corretamente no GitHub — sem confundir código-fonte com build e sem quebrar a estrutura do repositório.

Neste post, vou mostrar o fluxo simples e funcional que utilizo para enviar um projeto Hugo local para o GitHub usando o GitHub Desktop, evitando erros comuns.

 Estrutura correta do projeto

No meu ambiente, separo claramente código-fonte e build:

```bash
C:\Sites\
├── meublog-hugo           → código-fonte (Hugo)
└── willamistech.github.io → build final (HTML/CSS/JS)
```

- meublog-hugo contém content/, themes/, config.toml
- willamistech.github.io contém apenas arquivos estáticos gerados

Essa separação evita confusão e facilita manutenção futura.

## GitHub Desktop cuida do Git por você

Um ponto importante: não é necessário rodar git init manualmente quando se usa o GitHub Desktop.

O próprio GitHub Desktop:

- inicializa o repositório
- cria a branch main
- configura o remote (origin)
- faz o push para o GitHub

Isso reduz bastante a chance de erro, principalmente para quem está começando.

## Passo a passo para enviar o projeto Hugo ao GitHub

1. Abrir o GitHub Desktop
2. Clicar em File → Add local repository
3. Selecionar a pasta do projeto (ex: meublog-hugo)
4. Caso solicitado, clicar em Create repository here
5. Realizar o primeiro commit (Initial commit)
6. Clicar em Publish repository
7. Definir o nome do repositório no GitHub (ex: blog-hugo)
8. Publicar (público ou privado)

📌 Observação:
O nome exibido no GitHub Desktop será o nome da pasta local, e isso é normal.

## Erros comuns que devem ser evitados

- Criar um repositório dentro de outro
- Misturar código-fonte com build
- Forçar git add em pastas que não deveriam ser versionadas
- Criar o repositório no site antes de publicar pelo Desktop

Usar Hugo com GitHub Desktop é uma combinação simples, eficiente e profissional. Com uma boa organização de pastas e entendendo o papel de cada repositório, o versionamento deixa de ser um problema e passa a ser um aliado no aprendizado e na evolução técnica.