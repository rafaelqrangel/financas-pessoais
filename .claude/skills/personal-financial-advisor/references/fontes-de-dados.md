# Fontes de Dados — Planilhas, NotebookLM e Base Local

## 1. Planilhas do Google Drive (dados reais — fonte primária)

Acesse com as tools `mcp__Google_Drive__read_file_content` (passando o `fileId`) e `mcp__Google_Drive__search_files`. IDs verificados em 20/07/2026:

### ORCAMENTO CASA — planilha principal do orçamento familiar
- **fileId:** `1ueYEZ4HCoD9ZWjlbOz9YDclajvOAFnWQ34UcH0n1BJw`
- **Como ler:** o export markdown (`read_file_content`) achata as abas e embaralha tabelas. Prefira `download_file_content` com exportMimeType xlsx e leia com openpyxl (`data_only=True`), aba por aba.
- Abas: `__configs`, `GASTOS`, `GASTOS_FIXOS`, `FINANÇAS NOVO` (principal), `BANCO`, `BKP FINANÇAS NOVO`.

**Aba `FINANÇAS NOVO`** (a fonte central de custo de vida — indicada pelo Rafael em 20/07/2026):
- Bloco anual (linhas 2–31): col B = categoria de gasto, col C = total anual, cols D–O = meses 1–12 do ano corrente. Linha 3 = total geral.
- Bloco de fechamento mensal (linhas ~34–80): rateio do mês vigente entre Rafael e Marcela (percentuais na linha 36, hoje 52%/48%), fechamento de caixa individual nas linhas ~71–80 (Receita → custo casa → reembolsos/cartão → saldo do mês).
- Categorias grandes: FINANCIAMENTO VALOR, ESCOLA FILHOS, IPTU, SUPERMERCADO, DIARISTA, condomínio, contas de consumo, pets, MARINA CLUBE etc.

**Aba `BANCO`** (posição financeira e operacional de pagamentos):
- B1:H seção INVEST NUBANK (CDB 120%, valor atualizado; total em L3/L4 "Prova Real/Soma").
- B30–C33: receitas — salário bruto Rafael, salário bruto + funções Marcela; B44–D46: receita líquida, despesas e saldo de cada um.
- B31: VALOR REUNIDO ESCOLA MALU (fundo carimbado para escola).
- Colunas R–Y: fluxo de pagamentos do mês (origem, destino, pagador, status, data, valor).
- Colunas AG–AJ: extrato de lançamentos avulsos.

**Aba `GASTOS`** (lançamentos do app Semear, parcela a parcela):
- TITULAR DO GASTO, GASTO, VALOR TOTAL, VALOR TOTAL PARCELA, % PARCELA CONJUGE, VALOR PARCELA CONTA, PARCELA Nº, TOTAL PARCELAS, MÊS, ANO, DATA REGISTRO, PAGADOR.
- Cada linha é UMA parcela de UM gasto em UM mês — para comprometimento futuro, some parcelas com competência à frente.

### Investimentos fora de planilha (informados pelo Rafael em 20/07/2026)
- XP (Rafael): R$ 78.400 — composição a detalhar.
- Com Marcela: ~R$ 40.000 — onde está aplicado a confirmar.

### SEMEAR CASA - Dados — base normalizada (novo modelo)
- **fileId:** `1da5ovLYVA457M4cJsi1uJJOS2MXtxBJli5Aqw8PP_LE`
- Aba GASTOS com colunas: TIPO, DATA_REGISTRO, MES_REF, ANO_REF, CONTA, QUEM_ADIANTOU, DESCRICAO, VALOR_TOTAL, PARCELA_NUM, TOTAL_PARCELAS, VALOR_PARCELA, PERC_CONTA, VALOR_CONTA, CAT_MACRO, CAT_MICRO, STATUS, OBS.
- Preferir esta base quando estiver mais atualizada que a ORCAMENTO CASA (comparar `modifiedTime` antes de escolher).

### Assinaturas e Pagamentos de Rafael Rangel
- **fileId:** `1841i7mCQBaFZYCHgAP0sPycB9n7HjaCrxh2Bg64FPYo`
- Assinaturas mensais/anuais com status ATIVO/INATIVO e valores. Fonte primária do protocolo anti-sangria item 3 (recorrências).

### Faturas de cartão
- Arquivos xlsx avulsos no Drive (ex.: `fatura-aberta-final 0201-julho2026.xlsx`, pasta `1-ClbtZMbu3bO853E_xbXQFFPCEefpF_j`). Buscar por `title contains 'fatura'` quando precisar de detalhe transacional.

### Regras de leitura
- Sempre registre na resposta a data/hora da leitura dos dados ("fotografia de DD/MM").
- Valores podem estar como texto BR ("R$ 1.234,56") — normalize antes de somar.
- Se a busca não encontrar uma planilha esperada, procure variações antes de perguntar ao Rafael.
- Estas planilhas são a vida financeira real da família: leitura à vontade, escrita SÓ com pedido explícito do Rafael.

## 2. NotebookLM "Personal Financial Advisor" (base técnica)

O NotebookLM não tem API acessível daqui. A ponte é operada pelo Rafael, com o advisor no comando do que perguntar:

**Protocolo de consulta:**
1. Quando um tema exigir fundamento técnico profundo (tributação específica, produto complexo, regra de previdência, conteúdo dos livros/fontes que Rafael subiu lá), formule 1–3 perguntas PRONTAS PARA COLAR, específicas e fechadas — não "me fale sobre X", e sim "segundo as fontes, qual a diferença de tributação entre A e B para prazo de N anos?".
2. Entregue as perguntas em bloco de código para facilitar o copiar/colar.
3. Quando Rafael trouxer a resposta, integre-a à análise citando que a base veio do NotebookLM e grave o que for durável em `knowledge/notebooklm/` (um arquivo .md por tema).
4. Antes de gerar novas perguntas, verifique se `knowledge/notebooklm/` já cobre o tema — não faça Rafael repetir consulta.

## 3. Base local `knowledge/` (memória do advisor)

- `knowledge/perfil.md` — retrato financeiro da família: renda, dívidas, objetivos, prazos, decisões de perfil de risco. Atualize sempre que Rafael informar algo estrutural novo.
- `knowledge/decisoes.md` — log de decisões com data, contexto e número que a sustentou (ex.: "20/07/2026 — cancelar assinaturas X, Y: economia R$ 210/mês"). Toda decisão estrutural entra aqui.
- `knowledge/notebooklm/` — espelho das respostas técnicas trazidas do NotebookLM.

Manter esses arquivos atualizados é parte do trabalho: é o que dá continuidade entre sessões. Registre fatos e números, não transcrições de conversa.
