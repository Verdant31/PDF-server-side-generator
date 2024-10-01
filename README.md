# PDF Generator POC

Este projeto é uma **Proof of Concept (POC)** desenvolvida para resolver um problema específico de geração de PDFs dinâmicos com base no payload de uma requisição. Ele utiliza **Puppeteer** e **Handlebars** como parte da stack escolhida.

## Problema

A necessidade original era gerar um PDF contendo:

- Um **header** dinâmico
- Um **footer** dinâmico
- Uma **tabela** com dados baseados no payload

O desafio principal foi garantir que o **header** e o **footer** fossem gerados dinamicamente e ajustados para cada página, sem serem sobrescritos pelo conteúdo da tabela, que podia variar em tamanho por conta das propriedades do payload.

O **Puppeteer** disponibiliza a customização de do footer e do header através da sua API, porém, o template que ele aceita é um template fixo para todas as páginas com HTML estático, não abrangendo a necessidade do projeto que seria diferentes headers/footers para diferentes contextos.

## Solução

A solução implementada envolve o mapeamento do payload para gerar o conteúdo de cada seção:

- **Header**
- **Footer**
- **Tabela**

O mapeamento agrupa o conteudo em formato de objeto de cada uma dessas seções, com esses objetos foi utilizado o **Handlebars** para injetar o HTML da união desses 3.
Após a injeção, foi utilizado a biblioteca **pdf-merger-js** para unir os 3 PDF's em apenas um.

## Stack

- **Node.js**
- **Puppeteer**: Para a geração e manipulação do PDF.
- **Handlebars**: Para template dinâmico do conteúdo (header, footer, tabela).
- **pdf-merger-js**: Para unir os PDF's gerados.

## Experiência

Este projeto foi também uma oportunidade de aprendizado, já que tanto **Puppeteer** quanto **Handlebars** eram ferramentas novas utilizadas no desenvolvimento. O objetivo principal era garantir a funcionalidade de gerar PDFs organizados, com headers e footers dinâmicos, ajustados de acordo com o conteúdo da tabela.

## Resultados

- A geração dinâmica de PDF foi um sucesso.
- O layout não é sofisticado, visto que o foco foi na implementação da funcionalidade.

## Como rodar o projeto

1. Clone este repositório.
2. Instale as dependências com `npm install`.
3. Envie uma requisição utilizando o arquivo "requests.http"
4. O PDF deve ser baixado na raiz do projeto.
