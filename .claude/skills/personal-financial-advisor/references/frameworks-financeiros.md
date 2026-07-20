# Frameworks Financeiros — Cálculos do Advisor

Fórmulas que sustentam as recomendações. Toda recomendação numérica cita qual framework usou e mostra a conta.

## 1. Patrimônio de independência financeira (número-alvo)

O número central do método Cerbasi: quanto de patrimônio sustenta o custo de vida com renda passiva.

```
Patrimônio-alvo = Custo de vida anual / taxa real de retirada
```

- Taxa real conservadora no Brasil: 4% a 5% a.a. acima da inflação (juro real de títulos IPCA+ como referência observável).
- Exemplo: custo de vida de R$ 15.000/mês → R$ 180.000/ano → a 4,5% real: **R$ 4,0 milhões** em valores de hoje.
- Sempre apresente em valores reais (poder de compra de hoje), nunca nominais.

## 2. Projeção de aportes (a conta do tempo)

Valor futuro de aportes mensais `A` por `n` meses à taxa mensal `i`:

```
VF = A × [((1+i)^n − 1) / i]
```

Uso didático obrigatório: ao avaliar qualquer gasto recorrente, mostre o VF do mesmo valor aportado por 10 anos. É o argumento "custo em patrimônio" — o coração do estilo.

Taxa de referência didática: 10% a.a. nominal (≈0,797% a.m.) para exemplos rápidos; para planos formais, use juro real (IPCA+ vigente) e diga qual usou.

## 3. Ordem de prioridade do dinheiro (fila de alocação)

Cada real que sobra entra nesta fila — não pule etapas:

1. **Dívida cara** (juros > ~1,5% a.m.): quitar é retorno garantido e livre de imposto.
2. **Reserva de emergência**: 6× o custo fixo mensal da família (autônomo/CEO em transição: 12×). Liquidez diária, risco soberano (Tesouro Selic ou equivalente).
3. **Objetivos de curto prazo (< 3 anos)**: pós-fixado ou prefixado curto; não é dinheiro de bolsa.
4. **Patrimônio de longo prazo**: diversificação por classe (renda fixa real IPCA+, renda variável Brasil/exterior, imobiliário/FIIs) conforme perfil e prazo.
5. **Acelerações** (previdência com benefício fiscal, etc.): só depois da base montada.

## 4. Decisão de compra parcelada

Antes de qualquer parcelamento novo, calcule:

- **Comprometimento futuro**: total de parcelas já contratadas + a nova, mês a mês. Se algum mês futuro passar de ~30% da renda líquida em parcelas, a resposta padrão é "não agora".
- **Custo real**: preço à vista vs. parcelado. "Sem juros" com desconto à vista recusado É juro embutido — calcule a taxa implícita.
- **Teste do patrimônio**: o valor total investido a 10 anos (framework 2). Não para proibir — para decidir com o número na mesa.

## 5. Comparação de investimentos (protocolo mínimo)

Nunca compare por rentabilidade bruta. Sempre líquida de:

1. Imposto (tabela regressiva de renda fixa: 22,5% → 15%; isenções de LCI/LCA/debêntures incentivadas; come-cotas em fundos)
2. Taxas (administração, custódia, performance)
3. Inflação (transforme tudo em juro real)
4. Liquidez e prazo (o melhor investimento que você precisa resgatar na hora errada vira o pior)

Papel do advisor: ensinar o critério e apontar a classe de ativo adequada ao objetivo. Produto específico de corretora → decisão do Rafael, com o critério na mão. Fundamentos técnicos profundos → ponte com o NotebookLM (ver fontes-de-dados.md).

## 6. Regra do casal (Cerbasi, "Casais Inteligentes Enriquecem Juntos")

- Orçamento é da família, não de cada um: metas conjuntas antes de divisão de contas.
- A divisão Rafael/Marcela (percentuais na planilha) é operacional; o patrimônio-alvo é um só.
- Decisão estrutural (imóvel, carro, escola da Malu, mudança de padrão) exige conversa a dois com os números na mesa — o advisor prepara o material dessa conversa quando pedido.
- Cada um mantém uma verba livre pessoal sem prestação de contas — controle absoluto mata o plano no terceiro mês.
