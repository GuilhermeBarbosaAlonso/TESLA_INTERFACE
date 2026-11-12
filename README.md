# PULSO EV — Tesla vs. Resto do Mundo

Projeto acadêmico de interface web para apresentar uma análise de veículos elétricos registrados no estado de Washington, nos Estados Unidos. O site reúne indicadores, gráficos, storytelling e cuidados com a publicação dos dados, com foco em uma implementação simples em HTML, CSS e Bootstrap.

Apesar do título, a comparação entre a Tesla e as demais fabricantes utiliza um recorte regional. Os resultados não representam o mercado mundial nem vendas anuais.

## Objetivo

Transformar os resultados preparados em Python no Google Colab em uma interface organizada, responsiva e com recursos de acessibilidade, permitindo consultar os indicadores e compreender os limites da análise.

## Páginas

| Página | Conteúdo |
| --- | --- |
| `index.html` | Indicadores gerais, participação por fabricante e estatística descritiva. |
| `graficos.html` | Histograma, dispersão e boxplot, acompanhados de descrições e tabelas agregadas. |
| `storytelling.html` | Narrativa em quatro etapas sobre o recorte, a presença da Tesla, a diversidade de veículos e o comparativo BEV/PHEV. |
| `lgpd.html` | Princípios de privacidade, classificação qualitativa de risco dos campos e recomendações de publicação. |

## Tecnologias utilizadas

- **HTML5:** estrutura das páginas, navegação, imagens e tabelas.
- **CSS3:** personalização visual, cartões, foco visível e ajustes para telas pequenas.
- **Bootstrap 5.3.2:** grade responsiva e classes de layout, espaçamento e apresentação.
- **Bootstrap Icons 1.11.1:** ícones decorativos.
- **Python e Google Colab:** processamento dos dados e preparação dos gráficos antes da publicação.
- **Figma:** prototipação da interface.

A interface é estática: não possui back-end, banco de dados conectado, JavaScript próprio ou conexão ativa com o Google Colab. Os valores e imagens são carregados dos arquivos do projeto.

## Estrutura de arquivos

Organize a pasta da interface desta forma:

- `index.html`
- `graficos.html`
- `storytelling.html`
- `lgpd.html`
- `styles.css`
- `README.md`
- `imagens/`
  - `histograma.png`
  - `dispersao.png`
  - `boxplot.png`

Os quatro arquivos HTML e o CSS devem permanecer na mesma pasta. As imagens devem ficar dentro de `imagens`.

**Atenção aos nomes:** sufixos gerados durante downloads, como `index(2).html`, devem ser removidos para corresponder às referências do código. Use exatamente os nomes apresentados acima, inclusive letras minúsculas.

## Como executar

### Diretamente no navegador

1. Baixe os arquivos e organize as pastas conforme a estrutura indicada.
2. Abra `index.html` em um navegador atualizado.
3. Utilize o menu para acessar as demais páginas.
4. Mantenha conexão com a internet para carregar o Bootstrap e os ícones.

Não é necessário instalar Python, Node.js ou um banco de dados para abrir a interface. O CSV original e o notebook também não são necessários para a visualização dos resultados já publicados.

### No VS Code

1. Abra o VS Code.
2. Selecione **Arquivo > Abrir Pasta** e escolha a pasta do projeto.
3. Edite os arquivos HTML e o `styles.css` conforme necessário.
4. Abra `index.html` no navegador e atualize a página após salvar as alterações.

Opcionalmente, use uma extensão de servidor local, como Live Server, para facilitar a visualização durante a edição. Essa extensão não é obrigatória.

### Dependência de internet

O Bootstrap e o Bootstrap Icons são carregados por CDN. Sem internet, e sem os recursos disponíveis em cache, textos e imagens locais podem continuar acessíveis, mas a aparência e parte do comportamento responsivo serão afetadas. Para uma versão totalmente offline, será necessário baixar essas dependências e ajustar os caminhos nos quatro arquivos HTML.

## Como a interface foi construída

### Organização e navegação

Cada item do menu aponta para um arquivo HTML. A classe `active` destaca visualmente a página atual, e `aria-current="page"` comunica essa informação às tecnologias assistivas. Todas as páginas compartilham o mesmo arquivo CSS.

### Responsividade

Os indicadores usam a grade de 12 colunas do Bootstrap:

| Largura da janela | Classe aplicada | Organização |
| --- | --- | --- |
| Abaixo de 576 px | `col-12` | Um indicador por linha. |
| De 576 px até antes de 992 px | `col-sm-6` | Dois indicadores por linha. |
| A partir de 992 px | `col-lg-3` | Quatro indicadores por linha. |

O cabeçalho utiliza Flexbox e muda de coluna para linha a partir de 768 px. O CSS próprio complementa a adaptação com ajustes de espaçamento para janelas de até 600 px. As imagens usam `img-fluid`, e as tabelas ficam em contêineres `table-responsive`.

### Gráficos e atualização

Os gráficos são arquivos PNG preparados previamente. As barras de participação utilizam larguras percentuais definidas no HTML. Não existem filtros dinâmicos ou atualização automática. Os rótulos de localização e tipo de veículo indicam o contexto da análise.

## Dados e limites da análise

A fonte é o **Washington State Department of Licensing**, por meio da base *Electric Vehicle Population Data*. Os números publicados correspondem à versão do CSV utilizada pelo grupo, não a uma consulta atualizada ao portal.

| Indicador | Valor apresentado |
| --- | --- |
| Veículos no recorte de Washington, anos de modelo 2010–2025 | 259.847 |
| Participação da Tesla no recorte | 38,7% |
| Participação de King County | 47,7% |
| Registros com autonomia positiva utilizados nas estatísticas de autonomia | 98.212 |
| Média de autonomia elétrica de BEV, entre valores positivos | 200,36 milhas |
| Média de autonomia elétrica de PHEV, entre valores positivos | 31,70 milhas |

- **BEV:** veículo totalmente elétrico a bateria.
- **PHEV:** veículo híbrido com recarga externa.
- O ano do modelo não corresponde necessariamente ao ano da venda ou do registro.
- Valores ausentes ou não positivos foram excluídos das estatísticas de autonomia; isso não significa que os veículos tenham autonomia física igual a zero.
- A disponibilidade de autonomia varia entre os grupos e limita as comparações.
- Os resultados são descritivos e não demonstram, por si só, superioridade de uma fabricante ou evolução histórica de mercado.

## Recursos de acessibilidade

- Idioma da página identificado por `lang="pt-BR"`.
- Regiões semânticas de cabeçalho, navegação, conteúdo principal e rodapé.
- Títulos organizados em níveis.
- Link para pular o menu e acessar o conteúdo principal.
- Indicação de foco visível na navegação por teclado.
- Textos alternativos e legendas para os gráficos.
- Tabelas agregadas com cabeçalhos identificados por `scope`.
- Regiões de tabelas que podem receber foco pelo teclado.
- Controle nativo `details` e `summary` para consultar o resumo da dispersão.
- Informação de risco em texto, além das cores.

A **WCAG 2.2 nível AA é uma meta do projeto**. Os recursos implementados não equivalem a uma certificação. Ainda são necessários testes completos de teclado, contraste, zoom, leitores de tela e uso por pessoas.

## Privacidade e segurança

A interface apresenta resultados agregados e não publica VIN parcial, DOL Vehicle ID ou coordenadas individuais dos veículos. A versão atual não possui formulário de cadastro.

A página de LGPD utiliza finalidade, adequação e necessidade como referências acadêmicas. A classificação de risco foi proposta pelo grupo e não corresponde a categorias oficiais da lei. A origem da base é norte-americana; a página não determina a aplicação da legislação brasileira nem certifica conformidade jurídica.

A agregação reduz a exposição, mas não garante sozinha a impossibilidade de reidentificação. Informações individuais desnecessárias não devem ser incluídas nos arquivos públicos, mesmo que estejam ocultas por CSS.

## Como atualizar o trabalho

1. Revisar o recorte e os cálculos no notebook de análise.
2. Gerar novamente os gráficos e substituir os PNGs na pasta `imagens`.
3. Atualizar indicadores, barras, tabelas, descrições e storytelling nas páginas HTML.
4. Conferir se os valores apresentados nas quatro páginas são consistentes.
5. Revisar a publicação para evitar exposição de identificadores ou coordenadas.
6. Verificar links, imagens, layout em diferentes larguras e navegação por teclado.

Como o cabeçalho e o rodapé estão repetidos, alterações nesses elementos devem ser aplicadas aos quatro arquivos HTML.

## Verificações antes da apresentação

- Abrir `index.html` e testar todos os destinos do menu.
- Confirmar o carregamento das três imagens.
- Reduzir a janela e observar cartões, cabeçalho e tabelas.
- Usar Tab para conferir o foco e o link de pular para o conteúdo.
- Abrir o resumo agregado por ano e tipo na página de gráficos.
- Garantir acesso à internet para as bibliotecas externas.

Essas são verificações recomendadas para o computador da apresentação, não um registro de testes já aprovados.

## Referências

- [Base Electric Vehicle Population Data — Washington](https://data.wa.gov/Transportation/Electric-Vehicle-Population-Data/f6w7-q2d2)
- [Protótipo do grupo no Figma](https://www.figma.com/proto/3qhq1mumq5Kg9HTAvOx499?node-id=0-1)
- [Documentação do Bootstrap 5.3](https://getbootstrap.com/docs/5.3/)
- [Bootstrap Icons](https://icons.getbootstrap.com/)
- [MDN — HTML](https://developer.mozilla.org/pt-BR/docs/Web/HTML)
- [MDN — CSS](https://developer.mozilla.org/pt-BR/docs/Web/CSS)
- [WCAG 2.2 — W3C](https://www.w3.org/TR/WCAG22/)
- [Lei Geral de Proteção de Dados — Câmara dos Deputados](https://www2.camara.leg.br/legin/fed/lei/2018/lei-13709-14-agosto-2018-787077-normaatualizada-pl.html)

## Contexto acadêmico

Trabalho do grupo PULSO EV, desenvolvido no projeto **PCG Tesla vs. Resto do Mundo**, envolvendo análise de dados, prototipação e construção de uma interface web responsiva com recursos de acessibilidade.
