# Simulador de Investimentos em Fundos Imobiliários

Projeto desenvolvido como parte do desafio de Excel da DIO. A planilha funciona como uma ferramenta prática para simular aportes mensais em fundos imobiliários, estimar a evolução do patrimônio e visualizar uma sugestão de distribuição entre diferentes tipos de FII.

## Objetivo

O simulador foi criado para responder perguntas comuns de quem está planejando investir:

- Quanto posso investir por mês?
- Qual patrimônio posso acumular ao longo do tempo?
- Quanto desse patrimônio corresponde aos aportes e quanto corresponde aos rendimentos?
- Qual seria a estimativa de dividendos mensais?
- Como distribuir o aporte entre diferentes tipos de fundos imobiliários?

## Funcionalidades

- Cálculo automático da sugestão de investimento com base em 30% do salário informado.
- Simulação de patrimônio por aporte mensal, prazo e taxa de rendimento mensal.
- Estimativa de dividendos mensais a partir do rendimento da carteira.
- Comparação de cenários para 2, 5, 10, 20 e 30 anos.
- Seleção de perfil de investidor: Conservador, Moderado ou Agressivo.
- Distribuição automática do aporte entre seis categorias de FII.
- Projeção anual de 0 a 30 anos.
- Gráfico comparando o total investido com o patrimônio acumulado.

## Estrutura da planilha

### APP

É a tela principal do simulador. Nela, o usuário informa salário, aporte mensal, prazo, taxa de rendimento e perfil. A aba apresenta os principais resultados, cenários de longo prazo e a alocação sugerida da carteira.

![Tela principal do simulador](images/simulador-principal.png)

### Projeção

Apresenta a evolução anual do investimento e separa quatro informações: total aportado, patrimônio acumulado, rendimentos acumulados e dividendos mensais estimados.

![Projeção anual](images/projecao-anual.png)

### Planilha2

Contém a tabela de apoio utilizada para relacionar cada perfil de investidor aos percentuais sugeridos por tipo de FII.

## Fórmulas e conceitos utilizados

### Sugestão de aporte

```excel
=Salário*30%
```

### Patrimônio acumulado

Foi utilizada a função `FV`, que calcula o valor futuro de uma série de aportes mensais:

```excel
=FV(taxa_mensal; quantidade_de_anos*12; aporte_mensal*-1)
```

### Dividendos mensais estimados

```excel
=Patrimônio_acumulado*Rendimento_da_carteira
```

### Percentual por tipo de FII

O perfil selecionado é combinado com o tipo de FII para localizar o percentual correspondente na tabela de apoio:

```excel
=VLOOKUP(Perfil&"-"&Tipo_de_FII;Tabela_de_Perfis;4;FALSE)
```

### Valor destinado a cada categoria

```excel
=Percentual_sugerido*Aporte_mensal
```

## Como usar

1. Abra a aba `APP`.
2. Informe o salário e o rendimento mensal estimado da carteira.
3. Defina o aporte mensal, o prazo do investimento e a taxa de rendimento mensal.
4. Escolha o perfil de investidor na lista suspensa.
5. Consulte os resultados, os cenários e a distribuição sugerida.
6. Abra a aba `Projeção` para acompanhar a evolução anual e o gráfico comparativo.

## Aprendizados aplicados

Durante o desenvolvimento foram aplicados conceitos de referências absolutas, intervalos nomeados, validação de dados, funções financeiras, funções de busca, fórmulas condicionais, formatação de moeda e percentual, gráficos e organização visual de informações.

## Observação

Os resultados são simulações baseadas nas taxas informadas pelo usuário. Rentabilidade e dividendos podem variar ao longo do tempo, portanto a planilha não representa garantia de retorno nem recomendação individual de investimento.
