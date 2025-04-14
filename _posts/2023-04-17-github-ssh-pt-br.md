---
layout: post-pt-br
title: Chave SSH no github - Windows e Linux
seo_title: Como Gerar e Adicionar uma Chave SSH ao GitHub - Guia de Autenticação Segura
seo_description: Aprenda a gerar e adicionar uma chave SSH ao GitHub para autenticação segura. Siga nosso guia passo a passo com instruções detalhadas para usuários de Linux e Windows. Configure sua chave SSH no GitHub para facilitar operações como push e pull sem a necessidade de autenticação repetida. Otimize sua experiência no GitHub agora!
exerpt: Guia passo a passo sobre como gerar e adicionar uma chave SSH ao GitHub para autenticação segura. Aprenda a criar chaves SSH usando o algoritmo ED25519 com instruções detalhadas para Linux e Windows. Configure sua chave SSH no GitHub para facilitar operações como push e pull sem a necessidade de autenticação repetida.
cover_image: 'https://i.imgur.com/9GC9TvD.webp'
canonical_url: 'https://ryrden.github.io/old-website/2023-04-17-github-ssh-pt-br'
image_alt: 'Uma estatueta de um oktokat (Mascote do github) ao centro, ao fundo um laptop com a página principal do GitHub aberta.'
tags:
  - github
  - ssh
  - linux
  - windows
author: Ryan Souza
devto_url: 'https://dev.to/ryrden/chave-ssh-no-github-windows-e-linux-3gj6'
tabnews_url: null
comments: true
lang: pt-br
locale: pt_BR
published: true
id: 1572979
date: '2023-08-18T23:44:11Z'
---

- [O que é uma chave SSH?](#o-que-é-uma-chave-ssh)
- [Gerando uma chave SSH](#gerando-uma-chave-ssh)
  - [Linux](#linux)
  - [Windows](#windows)
- [Referências](#referências)

## O que é uma chave SSH?

Uma chave SSH é um par de chaves que são usadas para autenticar um usuário em um servidor. A chave pública é usada para criptografar os dados e a chave privada é usada para descriptografar os dados. A chave pública é compartilhada com o servidor e a chave privada é mantida em segredo pelo usuário.

existem diversos tipos de algoritmos de criptografia para gerar chaves SSH, mas neste tutorial eu vou ensinar como gerar uma chave SSH usando o algoritmo ED25519. O algoritmo ED25519 é um algoritmo de assinatura digital de curva elíptica que é considerado seguro e rápido.

para saber mais sobre o tema, eu indico esse artigo da Teleport: [Artigo](https://goteleport.com/blog/comparing-ssh-keys/) (em inglês)

## Gerando uma chave SSH

A partir de agora irei separar esse tutorial em duas partes, uma para Linux e outra para Windows.

Antes de começar, você precisa ter o git instalado em sua máquina. Se você não tem, indico a documentação oficial do git para instalar o git em sua máquina: [Documentação](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

### Linux

Para gerar uma chave SSH no Linux, você precisa abrir o terminal e digitar o seguinte comando:

```bash
ssh-keygen -t ed25519 -C <seu-email>
```

![ssh-keygen on linux](https://i.imgur.com/J56UKtq.webp)

Após digitar o comando, você vai ser solicitado a preencher alguns dados, como o nome da chave e a senha da chave. Você pode digitar o nome que quiser desde que não se esqueça dele, no meu caso, eu apenas apertei `enter` para que o git gerasse o nome da chave automaticamente e que a chave não tenha senha.

Com a chave gerada você deve copiar a chave pública para a área de transferência. Para isso, navegue ate a pasta onde a chave foi gerada (por padrão ela fica na pasta `~/.ssh`, como mostrado na imagem anterior) e digite o seguinte comando:

```bash
cat id_ed25519.pub
```

e copie a chave que aparecer na tela.

![getting the key in linux](https://i.imgur.com/nT9OTKx.webp)

Agora você precisa ir até a página de configurações do github e adicionar a chave que você acabou de copiar.

aqui um atalho para você ir direto para a página de configurações de chaves SSH do github: [Página de configurações de chaves SSH](https://github.com/settings/keys)

aqui você deve ir em `New SSH key` e cole a chave que você copiou anteriormente.

![paste key on github - linux](https://i.imgur.com/5L6KrD8.webp)

Clicando em Add SSH key, você vai adicionar a chave SSH ao github.

Pronto, agora é só testar se a chave foi adicionada corretamente e fazer dar clone de qualquer repositório que você tenha acesso sempre utilizando o endereço SSH. Para testar se a cahve foi adicionada corretamente, você pode digitar o seguinte comando:

```bash
ssh git@github.com
```

se tudo der certo, você vai ver uma mensagem de sucesso e você já pode fazer o clone de qualquer repositório que você tenha acesso, no meu caso eu fiz o clone do meu próprio repositório.

![Testing ssh key - linux](https://i.imgur.com/eDKiWUy.webp)

### Windows

Mesmo processo do linux com a exceção de que aqui eu usei o powershell para criar a chave SSH e o git bash para testar a chave SSH.

Primeiro você precisa abrir o powershell e digitar o seguinte comando:

```powershell
ssh-keygen -t ed25519 -C <seu-email>
```

substitua `<seu-email>` pelo seu email do github.

![ssh-keygen on windows](https://i.imgur.com/bCSWptA.webp)

Após digitar o comando, você vai ser solicitado a preencher alguns dados, como o nome da chave e a senha da chave. Você pode digitar o nome que quiser desde que não se esqueça dele, no meu caso, eu apenas apertei `enter` para que o git gerasse o nome da chave automaticamente e que a chave não tenha senha.

Com a chave gerada você deve copiar a chave pública para a área de transferência. Para isso, navegue ate a pasta onde a chave foi gerada (por padrão ela fica na pasta `C:\Users\ryans\.ssh`, como mostrado na imagem anterior) e digite o seguinte comando:

```powershell
type id_ed25519.pub
```

e copie a chave que aparecer na tela.

![getting ssh key in windows](https://i.imgur.com/XdeXkT1.webp)

Enfim, agora você precisa ir até a página de configurações do github e adicionar a chave que você acabou de copiar. aqui um atalho para você ir direto para a página de configurações de chaves SSH do github: [Página de configurações de chaves SSH](https://github.com/settings/keys)

aqui você deve ir em `New SSH key` e cole a chave que você copiou anteriormente.

![paste key on github - windows](https://i.imgur.com/fYitTGb.webp)

Clicando em Add SSH key, você vai adicionar a chave SSH ao github.

Agora basta verificar o funcionamento da chave SSH. Para isso, você precisa abrir o git bash e digitar o seguinte comando:

```bash
ssh git@github.com
```

se tudo der certo, você vai ver uma mensagem de sucesso e você já pode fazer o clone de qualquer repositório que você tenha acesso, no meu caso eu fiz o clone do meu próprio repositório.

![Testing ssh key - linux](https://i.imgur.com/OQaJNyj.webp)

## Referências

- [Documentação do Github](https://docs.github.com/pt/authentication/connecting-to-github-with-ssh)

Espero que esse tutorial tenha ajudado você a configurar a sua chave SSH no github. Se tiver alguma dúvida ou sugestão, deixe um comentário abaixo ou entre em contato comigo pelo [LinkedIn](https://www.linkedin.com/in/ryan25/) ou pela aba de [contato](https://ryrden.github.io/old-website/contact/) do meu site.
