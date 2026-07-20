# Fontes de Dados — Planilhas, NotebookLM e Base Local

## 1. Planilhas do Google Drive (dados reais — fonte primária)

Acesse com as tools `mcp__Google_Drive__read_file_content` (passando o `fileId`) e `mcp__Google_Drive__search_files`. IDs verificados em 20/07/2026:

### ORCAMENTO CASA — planilha principal do orçamento familiar
- **fileId:** `1ueYEZ4HCoD9ZWjlbOz9YDclajvOAFnWQ34UcH0n1BJw`
- Abas conhecidas: `__configs` (metadados do app Semear / formulário de gastos), `GASTOS` (lançamentos parcela a parcela).
- Estrutura de GASTOS: TITULAR DO GASTO, GASTO, VALOR TOTAL, VALOR TOTAL PARCELA, % PARCELA CONJUGE, VALOR PARCELA CONTA, PARCELA Nº, TOTAL PARCELAS, MÊS, ANO, DATA REGISTRO, PAGADOR.
- Cada linha é UMA parcela de UM gasto em UM mês — para totais mensais, agrupe por MÊS/ANO; para comprometimento futuro, some parcelas com competência à frente.
- `% PARCELA CONJUGE` define a divisão Rafael/Marcela; `VALOR PARCELA CONTA` é o que efetivamente sai da conta indicada.

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
