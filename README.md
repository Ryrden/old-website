# Website

[![wakatime](https://wakatime.com/badge/user/ed84c523-3e63-43f7-b210-066a9dd37830/project/3d3557bb-1c2b-424e-ad80-a6354f2cabe1.svg)](https://wakatime.com/badge/user/ed84c523-3e63-43f7-b210-066a9dd37830/project/3d3557bb-1c2b-424e-ad80-a6354f2cabe1)
![GitHub repo size](https://img.shields.io/github/repo-size/ryrden/old-website)
![GitHub language count](https://img.shields.io/github/languages/count/ryrden/old-website)

<img src="https://github.com/Ryrden/old-website/assets/76923948/627f01b8-98bd-4024-b518-ecca52ca8186" alt="printscreen da primeira tela">

> Esse é o meu website pessoal, onde eu mostro um pouco sobre mim e meus projetos.

## 💻 Pré-requisitos

Antes de começar, verifique se você atendeu aos seguintes requisitos:
<!---Estes são apenas requisitos de exemplo. Adicionar, duplicar ou remover conforme necessário--->
* Você instalou a versão mais recente de `Jekyll` e `Ruby`, caso não tenha, [clique aqui](https://jekyllrb.com/docs/installation/).

## 🚀 Instalando <website>

Para instalar o <website>, siga estas etapas:

```
bundle install
```

## ☕ Usando <website>

Para usar <website>, siga estas etapas:

```
bundle exec jekyll serve
```

## 🗂 Estrutura de pastas

### 📋 Conteúdo

* `_posts`: Posts (Meus artigos). Devem ser criados dentro da pasta da respectiva categoria, e com data no nome (exemplo: 2022-01-05-titulo-exemplo.md). Escreva preferencialmente em markdown.

### 🎨 Disposição e estilos

* `_data`: Dados estruturados para serem reusados no site. Por exemplo lista de navegação da navbar ou minhas redes sociais.

* `_includes`: Componentes que podem ser reusados entre páginas.

* `_layouts`: Layouts base para cada tipo de página. Atualmente existe o default (usado ou herdado em todas as páginas) e post (usado para publicações de artigos).

* `_sass`: Arquivos SASS (.scss ou .sass) para definir estilos. Essa pasta é especificamente para arquivos de estilo a serem "incluidos".
assets Arquivos que serão servidos na pasta assets, inclui favicon e estilização principal (que importa arquivos da _sass).

### 📊 Configurações e CI/CD

* `_config.yml`: Configurações do site.

## 📫 Contribuindo para <website>

Para contribuir com <website>, siga estas etapas:

1. Bifurque este repositório.
2. Crie um branch: `git checkout -b <nome_branch>`.
3. Faça suas alterações e confirme-as: `git commit -m '<mensagem_commit>'`
4. Envie para o branch original: `git push origin <website> / <local>`
5. Crie a solicitação de pull.

Como alternativa, consulte a documentação do GitHub em [como criar uma solicitação pull](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request).

## 📝 Licença

Esse projeto está sob licença. Veja o arquivo [LICENÇA](LICENSE) para mais detalhes.

[⬆ Voltar ao topo](#website)<br>
