# Dashboard de Vendas Porsche

## 1. Visão geral

Projeto de dashboard interativa para explorar vendas de veículos
Porsche. Foi desenvolvida em HTML, CSS e JavaScript, com gráficos em
Chart.js e dados incorporados ao arquivo HTML. Os filtros atualizam
indicadores, gráficos e tabela.

## 2. Perguntas de negócio escolhidas e justificativas

  -----------------------------------------------------------------------
  Pergunta                            Por quê?
  ----------------------------------- -----------------------------------
  Quantas vendas existem no recorte   Dimensionar o volume comercial do
  selecionado?                        conjunto filtrado.

  Qual é o faturamento total?         Avaliar o valor financeiro das
                                      vendas no recorte.

  Qual é o preço médio dos veículos?  Comparar o valor médio das
                                      transações entre modelos, anos e
                                      localidades.

  Qual modelo lidera em quantidade de Identificar os modelos com maior
  vendas?                             volume comercial; todos os
                                      empatados na liderança são
                                      exibidos.

  Como as vendas se distribuem por    Identificar concentração geográfica
  cidade?                             e localidades relevantes.

  Como o volume varia por ano do      Comparar os anos de modelo
  modelo?                             representados na base.

  Como as formas de pagamento se      Comparar os meios de pagamento por
  relacionam com volume e             número de vendas e valor
  faturamento?                        financeiro.

  Quais são os registros individuais  Permitir conferência e investigação
  de um recorte?                      com pesquisa, ordenação e
                                      paginação.
  -----------------------------------------------------------------------

### Indicadores e visualizações

-   **KPIs:** vendas filtradas, faturamento total, preço médio e modelo
    líder.
-   **Geografia:** vendas por cidade; ao selecionar uma cidade, a
    visualização detalha os modelos vendidos nela.
-   **Tempo:** vendas por ano do modelo.
-   **Pagamento:** quantidade de vendas e faturamento por forma de
    pagamento.
-   **Detalhamento:** tabela pesquisável, ordenável e paginada.

Os filtros combináveis são modelo, ano do modelo, estado, cidade e forma
de pagamento. O estado restringe as cidades disponíveis.

## 3. Prompt utilizado e evolução até a versão final

O desenvolvimento foi iterativo: primeiro foram definidas as perguntas
de negócio; depois, os filtros, visualizações, regras de cálculo e
requisitos de validação.

### Prompt consolidado da versão final

> Desenvolva uma dashboard interativa de vendas Porsche em um único
> arquivo HTML, usando HTML, CSS, JavaScript e Chart.js. Incorpore os
> dados da planilha tratada ao próprio arquivo. Use um visual esportivo,
> profissional e responsivo, com tema escuro e detalhes em vermelho.
>
> Disponibilize filtros combináveis para modelo Porsche, ano do modelo,
> estado, cidade e forma de pagamento. O filtro de estado deve
> restringir as cidades disponíveis; se uma cidade selecionada deixar de
> ser válida após a alteração do estado, limpe a seleção de cidade.
>
> Exiba quantidade de vendas filtradas, faturamento total, preço médio e
> modelo líder. Calcule o preço médio apenas com preços numéricos
> válidos. Use a quantidade de vendas do conjunto filtrado como
> denominador de percentuais. Em caso de empate na liderança de modelos,
> exiba todos os modelos empatados.
>
> Inclua visualizações de vendas por cidade, com detalhamento por modelo
> quando uma cidade estiver selecionada; vendas por ano do modelo; e
> quantidade de vendas e faturamento por forma de pagamento, com escalas
> adequadas às duas métricas.
>
> Inclua uma tabela com pesquisa, ordenação por coluna e paginação.
> Trate filtros sem resultados, valores ausentes e preços inválidos sem
> quebrar a interface. Confira a quantidade de registros carregados em
> relação à base esperada. Deixe explícita qualquer suposição sobre a
> moeda quando ela não estiver informada na fonte.

### O que mudou até a versão final

1.  **Perguntas de negócio:** a ideia inicial foi organizada em análises
    comerciais, financeiras, geográficas, temporais e por forma de
    pagamento.
2.  **Filtros:** foram definidos cinco filtros combináveis: modelo, ano
    do modelo, estado, cidade e forma de pagamento.
3.  **Regras de cálculo:** a média considera apenas preços numéricos
    válidos; o denominador de percentuais é o total de vendas filtradas;
    todos os líderes empatados devem ser exibidos.
4.  **Dependência entre filtros:** o estado restringe a lista de
    cidades, evitando combinações incompatíveis.
5.  **Gráficos e tabela:** foram especificadas três visualizações e uma
    tabela pesquisável, ordenável e paginada.
6.  **Validação:** foram acrescentados requisitos para estados vazios,
    preços inválidos e conferência da quantidade de registros.
7.  **Implementação:** os dados foram incorporados ao HTML. A biblioteca
    Chart.js é carregada por CDN e exige internet para renderizar os
    gráficos.

O texto acima é uma especificação consolidada representativa do prompt
final, não uma transcrição literal de cada mensagem intermediária.

## 4. Tratamento da base antes do uso pela IA

A fonte foi `porsche_database_sanitized(1).xlsx`, na aba `Sanitized`,
com 100 registros e 12 colunas.

### Campos usados

-   `sale_id`: identificador da venda;
-   `PorscheModelSanitized`: modelo;
-   `ModelYearSanitized`: ano do modelo;
-   `SalesPriceSanitized`: preço;
-   `PayMethodSanitized`: forma de pagamento;
-   `CitySanitized`: cidade;
-   `StateSanitized`: estado.

### Preparação e verificações

-   A estrutura da aba e os campos relevantes foram inspecionados.
-   Foram selecionadas as colunas necessárias para filtros, KPIs,
    gráficos e tabela.
-   Os preços foram verificados como numéricos e não nulos nesta versão
    da base. A regra da média, ainda assim, considera somente valores
    numéricos válidos.
-   A dashboard verifica a quantidade esperada de registros, usando 100
    como referência para esta versão.
-   Os filtros categóricos são construídos a partir dos valores
    encontrados nos dados.
-   A planilha não declara explicitamente a moeda. A formatação em dólar
    americano usada na versão atual é provisória e precisa ser
    confirmada ou ajustada antes da publicação definitiva.
-   A origem já se identifica como sanitizada. O desenvolvimento não
    dependeu de uma limpeza extensa adicional; o trabalho consistiu
    principalmente em inspeção, seleção de campos, validação básica e
    incorporação dos dados ao HTML.

## 5. Ferramentas e método

O projeto foi desenvolvido com **ChatGPT em uma conversa textual**, por
meio de refinamento iterativo dos requisitos e geração do HTML.

-   **ChatGPT com Canvas:** não foi utilizado.
-   **Agente com skill:** não foi utilizado.
-   **Método:** definição das perguntas de negócio, detalhamento de
    filtros e visualizações, formalização das regras de cálculo e
    geração/validação do arquivo HTML.

Tecnologias: HTML, CSS, JavaScript e Chart.js. Os dados estão
incorporados ao HTML, mas o Chart.js é carregado por CDN.

## 6. Endereço da dashboard publicada

**Status:** foi gerado o arquivo HTML, mas ainda não há endereço público
de hospedagem confirmado.

-   **Arquivo:** `dashboard_porsche.html`
-   **URL pública:** a definir após a hospedagem.

Para disponibilizar a dashboard na internet, publique o HTML em um
serviço de páginas estáticas, como GitHub Pages, Netlify ou Vercel, e
substitua esta seção pela URL pública definitiva. Não se deve apresentar
o caminho local do arquivo como se fosse um endereço público.

## 7. Como executar localmente

1.  Salve `dashboard_porsche.html` em uma pasta local.
2.  Abra o arquivo em um navegador moderno.
3.  Mantenha a conexão com a internet ativa para carregar Chart.js pela
    CDN.
4.  Use os filtros para atualizar indicadores, gráficos e tabela.

## 8. Limitações e próximos passos

-   Confirmar a moeda correta dos preços.
-   Publicar o arquivo em um serviço de hospedagem e registrar a URL
    pública.
-   Validar os indicadores com a área de negócio antes de usar os
    resultados para decisões oficiais.
-   Ao atualizar a base, revisar a contagem esperada e regenerar os
    dados incorporados.
-   Se houver atualizações frequentes, considerar separar dados e
    interface e automatizar a atualização.

## Resumo técnico

  Item                   Descrição
  ---------------------- ------------------------------------------------------------
  Fonte                  `porsche_database_sanitized(1).xlsx`, aba `Sanitized`
  Registros analisados   100
  Arquivo                `dashboard_porsche.html`
  Tecnologias            HTML, CSS, JavaScript e Chart.js
  Filtros                Modelo, ano do modelo, estado, cidade e forma de pagamento
  Hospedagem pública     https://n3arvana.github.io/dashboard_porsche_sales/
