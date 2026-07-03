 📘 Miniguia de Estudos — Renda Fixa vs. Renda Variável 

Projeto prático do desafio **"Explorando a IA como Ferramenta de Aprendizagem Ativa"** (DIO), no qual utilizei o **NotebookLM** para construir um caderno temático sobre investimentos básicos, aplicando curadoria de fontes, engenharia de prompts e organização do conhecimento.

---

## 🎯 1. Contexto e Objetivos

### Assunto escolhido
**Investimentos básicos: Renda Fixa vs. Renda Variável.** Escolhi esse tema por ser a porta de entrada para qualquer pessoa que queira sair da caderneta de poupança e começar a investir de forma consciente, entendendo risco, liquidez e rentabilidade antes de tomar decisões.

### Objetivos de estudo
1. Compreender a diferença conceitual entre renda fixa e renda variável (previsibilidade de retorno vs. risco/volatilidade).
2. Identificar os principais instrumentos de cada categoria (CDB, Tesouro Direto, LCI/LCA vs. ações, fundos imobiliários, ETFs).
3. Relacionar indicadores econômicos e fatores de risco (taxa de juros, indexadores, risco de crédito) com a rentabilidade da renda fixa.
4. Entender como o perfil de investidor (conservador, moderado, arrojado) orienta a escolha entre as duas categorias.
5. Construir um vocabulário técnico mínimo para leitura autônoma de conteúdos financeiros.

---

## 📚 2. Curadoria de Fontes

Selecionei 3 fontes abertas e institucionais (bolsa e órgãos reguladores), evitando blogs comerciais, para garantir informação confiável e sem viés de venda de produto. Todas foram adicionadas como *sources* no caderno do NotebookLM.

| # | Fonte | Tipo | Link |
|---|-------|------|------|
| 1 | B3 Educação — Trilha *Começando a investir do zero* | Página web | https://edu.b3.com.br/w/trilha-comecando-a-investir-do-zero |
| 2 | CVM — Caderno do Investidor nº 3: Fundos de Investimento (*caderno cvm.pdf*) | PDF | https://www.gov.br/investidor/pt-br/educacional/publicacoes-educacionais/cadernos/cvm-caderno-03-3ed.pdf |
| 3 | Banco Central do Brasil — Caderno de Educação Financeira: Gestão de Finanças Pessoais (*caderno_cidadania_financeira.pdf*) | PDF | https://www.bcb.gov.br/pre/pef/port/caderno_cidadania_financeira.pdf |


---

## 🔧 3. Engenharia de Prompts e "Cicatrizes"

Aqui documento as perguntas estratégicas, as variações de prompt testadas, as respostas obtidas e as dificuldades encontradas no caminho — a parte mais valiosa do processo.

### 3.1 Perguntas estratégicas elaboradas

1. Com base nas fontes, explique a diferença entre renda fixa e renda variável em até 3 frases, citando exemplos de cada uma.
2. Baseado apenas em uma fonte específica, o que é renda fixa?
3. Explique um conceito técnico como se eu tivesse 15 anos, usando as fontes carregadas.
4. Liste diferenças entre renda fixa e renda variável em formato de tabela.
5. As fontes divergem ou se complementam sobre um determinado ponto (ex: riscos)?

### 3.2 Variações de prompt testadas

| Variação | Prompt exato | Resposta obtida (resumo) | Fontes citadas | Dificuldade / observação |
|---|---|---|---|---|
| **A** — Pergunta aberta | "Com base nas fontes, explique a diferença entre renda fixa e renda variável em até 3 frases, citando exemplos de cada uma." | Renda fixa tem remuneração definida por taxas/índices desde o início (ex: Tesouro Direto, CDBs, debêntures); renda variável tem retorno imprevisível e mais risco (ex: ações, FIIs, BDRs); a diferença central é a previsibilidade do retorno. | Citou as fontes da B3 e da CVM | Resposta direta e correta; boa como pergunta de abertura para introduzir o tema |
| **B** — Restrita a 1 fonte | "Baseado apenas no caderno_cidadania_financeira.pdf, o que é renda fixa?" | Renda fixa paga remuneração conforme taxa de juros (pré ou pós-fixada); risco principal é o de crédito; exemplos citados: fundos de renda fixa, poupança, títulos públicos. | Citou as 3 fontes, não só a pedida | **Dificuldade real:** mesmo pedindo explicitamente "apenas" uma fonte no texto do prompt, o modelo misturou as três fontes na resposta. *Solução:* desmarcar as demais fontes na barra lateral (checkbox) antes de perguntar, em vez de confiar só na instrução em texto |
| **C** — Nível de linguagem | "Explique o que é renda fixa como se eu tivesse 15 anos, usando as fontes carregadas." | Usa analogia de empréstimo com "aluguel" (juros); explica prefixado vs. pós-fixado; cita exemplos (Tesouro Direto, CDB, poupança); liga ao perfil conservador; explica risco de crédito. | Citações numeradas de 1 a 6 | Linguagem ficou simples sem perder precisão técnica — funcionou bem. **Observação:** a numeração das citações não corresponde 1:1 às 3 fontes da lista lateral (o NotebookLM numera por trecho, não por documento), o que confunde um pouco a rastreabilidade |
| **D** — Formato estruturado | "Liste 5 diferenças entre renda fixa e renda variável em formato de tabela." | Tabela com colunas Renda Fixa / Renda Variável, cobrindo Definição, Previsibilidade, Fatores de Risco, Perfil do Investidor e Exemplos de Ativos. | Cruzou várias fontes (citações 1 a 5) | Foi a resposta mais completa e organizada de todas — ótimo prompt para gerar material de revisão rápida (flashcards) |
| **E** — Cruzamento entre fontes | "As fontes divergem ou se complementam sobre os riscos da renda variável? Explique." | Conclusão: as fontes se complementam, não divergem. Cobre previsibilidade/incerteza, magnitude do risco, relação risco x retorno, severidade das perdas (podem superar o capital aplicado) e perfil do investidor. | Nomeou explicitamente `caderno_cvm.pdf` e `caderno_cidadania_financeira.pdf`, com citações de 1 a 9 | Foi o prompt que melhor cruzou as fontes — nomear os documentos explicitamente na resposta (e não só numerar) ajudou bastante na rastreabilidade da informação |

### 3.3 Principais dificuldades (troubleshooting)

- **"Apenas esta fonte" nem sempre é respeitado.** Pedir no texto do prompt para usar só um documento não garante que o modelo ignore os demais — ele pode misturar informações de todas as fontes carregadas mesmo assim. *Solução que funciona de verdade:* desmarcar as fontes indesejadas na checkbox da barra lateral esquerda antes de perguntar.
- **Numeração de citação ≠ número de fontes.** Com apenas 3 documentos carregados, apareceram citações numeradas até 6 ou 9 — porque o NotebookLM numera por trecho citado, não por fonte. É preciso clicar em cada número para conferir a qual documento ele realmente se refere.
- **Prompts abertos geram respostas mais "seguras" e genéricas**, enquanto prompts que pedem formato específico (tabela) ou comparação explícita entre fontes ("divergem ou se complementam") extraem respostas mais ricas e melhor referenciadas. Vale sempre ser específico sobre o formato e o nível de cruzamento de fontes desejado.

---

## 📖 4. Miniguia de Estudo (Entrega Final)

### 4.1 Resumos estruturados

**Renda Fixa — conceito e características**
Um investimento é considerado renda fixa quando as regras de remuneração (taxa ou índice de referência) já são conhecidas no momento da aplicação. Pode ser prefixada (retorno definido desde a compra) ou pós-fixada (calculada no momento do resgate, com base em um indexador definido previamente). Os principais exemplos são Tesouro Direto, CDB, LCI/LCA, debêntures e caderneta de poupança. O principal risco associado é o **risco de crédito** — a chance de a instituição para quem você emprestou o dinheiro não conseguir pagar de volta.

**Renda Variável — conceito e características**
Na renda variável, a rentabilidade não é dimensionada nem prevista no momento da aplicação, e depende das oscilações do mercado. Envolve riscos maiores que a renda fixa, incluindo a possibilidade de rentabilidade negativa — em algumas estratégias, as perdas podem inclusive superar o capital aplicado. Em troca desse risco maior, o investidor busca uma expectativa de retorno mais elevado. Exemplos: ações, BDRs, fundos imobiliários (FII), ETFs e criptoativos.

**Previsibilidade como diferença central**
A principal diferença entre as duas categorias está na previsibilidade: na renda fixa, as regras do "jogo" (taxa, prazo, forma de remuneração) são combinadas logo no início; na renda variável, o retorno depende do desempenho do ativo e das oscilações de mercado, sendo conhecido apenas no momento do resgate.

**Perfil de investidor**
As fontes convergem em relacionar o perfil de investidor ao tipo de ativo mais adequado: a renda fixa é mais compatível com o perfil **conservador**, que prioriza segurança e menor volatilidade; a renda variável é mais compatível com perfis **moderado e arrojado**, que aceitam mais risco em troca de expectativa de ganhos maiores.

**Complementaridade entre fontes**
Ao comparar os documentos, não há divergência entre eles sobre os riscos da renda variável — pelo contrário, se complementam: enquanto um caderno aprofunda o conceito de imprevisibilidade da rentabilidade, o outro detalha que certas estratégias podem gerar perdas superiores ao capital investido, obrigando o investidor a aportar recursos extras.

### 4.2 Glossário

| Termo | Definição resumida |
|---|---|
| **Renda Fixa** | Investimento cuja forma de remuneração é conhecida no momento da aplicação (pré ou pós-fixada). |
| **Renda Variável** | Investimento cujo retorno não é conhecido previamente e varia conforme o mercado/desempenho do ativo. |
| **Taxa Prefixada** | Modalidade em que o valor do rendimento é estipulado no momento da aplicação. |
| **Taxa Pós-fixada** | Modalidade em que o rendimento é calculado no resgate, com base em um indexador definido previamente. |
| **Risco de Crédito** | Risco de a instituição emissora do título não conseguir honrar o pagamento. |
| **CDB** | Certificado de Depósito Bancário; título de renda fixa emitido por bancos. |
| **LCI / LCA** | Letras de Crédito Imobiliário/do Agronegócio; títulos de renda fixa isentos de IR para pessoa física. |
| **Tesouro Direto** | Programa do governo para venda de títulos públicos federais a pessoas físicas. |
| **Debêntures** | Títulos de dívida emitidos por empresas para captar recursos. |
| **Ações** | Frações do capital social de uma empresa; representam participação societária (renda variável). |
| **BDR** | Brazilian Depositary Receipt; recibo negociado no Brasil que representa ações de empresas estrangeiras. |
| **FII (Fundo Imobiliário)** | Fundo que investe em imóveis ou títulos ligados ao setor imobiliário, negociado em bolsa. |
| **Perfil de investidor** | Classificação (conservador, moderado, arrojado) conforme a tolerância a risco. |
| **Rentabilidade negativa** | Situação em que o investimento perde valor, podendo, em certas estratégias de renda variável, superar o capital aplicado. |

### 4.3 Prompts reutilizáveis para futuras revisões

```text
1. Resumo rápido:
"Resuma em até 5 bullet points o conceito de [tema] com base apenas nas fontes carregadas."

2. Comparação em tabela:
"Liste as principais diferenças entre [conceito A] e [conceito B] em formato de tabela,
usando apenas as fontes carregadas."

3. Explicação simplificada:
"Explique [tema] como se eu tivesse 15 anos, usando as fontes carregadas."

4. Cruzamento entre fontes:
"As fontes divergem ou se complementam sobre [tema]? Explique."

5. Restrição a uma única fonte (desmarcando as demais na barra lateral):
"Baseado apenas nesta fonte, o que ela diz sobre [tema]?"

6. Autoteste:
"Crie 5 perguntas de múltipla escolha sobre [tema] com base nas fontes,
incluindo gabarito e a fonte de cada resposta."
```

---

## 🧠 5. Reflexão final

Esse exercício mostrou o valor do NotebookLM como ferramenta de **aprendizagem ativa**: em vez de receber respostas prontas, a curadoria das fontes, a formulação de perguntas estratégicas e os testes de variações de prompt exigem pensamento crítico constante. Um achado importante foi perceber que instruções de restrição de fonte escritas em texto livre  — é preciso usar os controles da própria interface (seleção de fontes) para garantir isso de fato. Isso reforça o hábito de verificação: a IA funciona aqui como uma interface de navegação e síntese sobre material previamente validado, não como fonte de verdade absoluta.
Sobre a plataforma, gerar os testes para validar o conhecimento com base nas fontes, é algo que achei sensacional.

---

## 🛠️ Tecnologias utilizadas
- [NotebookLM](https://notebooklm.google.com/) — geração de resumos e Q&A com citação de fontes
- Markdown — documentação do repositório

---

## 👤 Autor
*Fernanda Fernandes Bezerra*   — projeto desenvolvido para o desafio de projeto da [DIO](https://www.dio.me/).
