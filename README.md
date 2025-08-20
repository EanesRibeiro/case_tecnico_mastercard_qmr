# Case Técnico Flash - Análise de Dados Mastercard QMR

## 🎯 Resumo do Desafio

Este projeto corresponde à resolução de um **case técnico de análise de dados** da Flash, com foco no "Mastercard Quarterly Management Reporting" (QMR).  

O objetivo principal foi **responder às questões propostas no desafio**, que envolvem:

1. Construir as métricas trimestrais do QMR (cartões ativos, novos, terminados, bloqueados e com transações).
2. Analisar a adoção de cartões **Contactless vs. PIN** e sugerir estratégias para aumentar a penetração de Contactless.
3. Explorar dados de bloqueios e cartões expirando para propor **recomendações estratégicas** que otimizem a gestão do portfólio e reduzam riscos.

---

## 🛠️ Metodologia

O projeto foi dividido em etapas:

1. **Organização do Projeto**
   - Diretórios: `data/`, `notebooks/`, `outputs/`.
   - Arquivos principais: `EDA.ipynb` (análise exploratória e resolução do case).

2. **Exploração e Limpeza dos Dados (EDA)**
   - Carregamento das tabelas `cards`, `cards_status`, `cards_transactions`.
   - Verificação de duplicatas, nulos e consistência entre chaves.
   - Conversão de colunas de data para `datetime`.
   - Criação da função `get_status_on_date(card_number, ref_date)` para determinar status de cartões em uma data de referência.

3. **Questão 1 – Relatório QMR**
   - Construção de um DataFrame consolidado para Q1, Q2 e Q3/2023.
   - Cálculo das métricas:
     - Cards at Beginning of Quarter (Open / Blocked).
     - New Cards Obtained During Quarter.
     - Cards Terminated During Quarter.
     - Cards at End of Quarter (Open / Blocked).
     - Cards with at Least One Transaction.
   - Validação da equação: `End ≈ Beginning + New - Terminated`.

4. **Questão 2 – Análise Contactless vs. PIN**
   - Percentual de cartões Contactless no final do Q3/2023.
   - Segmentação das top empresas com maior volume de cartões PIN.
   - Identificação de cartões PIN próximos da expiração → candidatos para upgrade.
   - Visualizações: gráfico de pizza (Contactless vs. PIN) e barras (Top Empresas com PIN).

5. **Questão 3 – Insights Estratégicos**
   - Análise de cartões “temporarily blocked” sem mudança de status relevante em trimestres subsequentes.
   - Cálculo do tempo médio de bloqueio e estimativa do impacto em receita.
   - Identificação de cartões expirando no Q4/2023.
   - Formulação de recomendações estratégicas: renovação automática, campanhas de reengajamento, upgrade para Contactless.

6. **Visualizações**
   - Gráficos de linha para evolução das métricas QMR.
   - Gráficos de barras empilhadas (Open vs. Blocked).
   - Outputs armazenados em `outputs/`.

---

## 📊 Resultados Chave

### Relatório QMR (Q1–Q3 2023)

| Quarter | Cards at Beginning (Open) | Cards at Beginning (Blocked) | New Cards Obtained | Cards Terminated | Cards at End (Open) | Cards at End (Blocked) | Cards with ≥1 Transaction |
| :--- | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| Q1 2023 | 158,599 | 1,168 | 90 | 4,686 | 181,508 | 5,373 | 126,560 |
| Q2 2023 | 181,508 | 5,373 | 91 | 8,687 | 215,200 | 5,681 | 153,578 |
| Q3 2023 | 215,200 | 5,681 | 92 | 11,061 | 251,915 | 6,092 | 173,232 |

### Contactless vs. PIN (Q3/2023)

- **Contactless:** 201,027 (79.8%)
- **PIN:** 50,888 (20.2%)

### Top 10 Empresas com Maior Volume de Cartões PIN

| Company_ID | # Cartões PIN |
| :--- | ---: |
| 5e5845d509555e0007d06483 | 575 |
| 5d9408e9b0d899000754c19b | 575 |
| 5f15f3ed20f6540008628942 | 499 |
| 6023d0e9f22b98000701db6f | 392 |
| 60d1f118462483000902d83d | 284 |
| 602faf45145da600073b1b1f | 256 |
| 5f299d66b18f850008c4e289 | 249 |
| 60509c5a9964610007cc0031 | 243 |
| 61489736429d920009ff62eb | 242 |
| 60d9d19a7751350008fcb408 | 208 |

---

## 💡 Recomendações de Negócio

1. **Bloqueios**
   - Implementar alertas para bloqueios prolongados.
   - Criar fluxos de reativação proativa para reduzir perda de receita.

2. **Adoção Contactless**
   - Incentivar upgrades de PIN próximos da expiração.
   - Focar em empresas com maior volume de PIN para impacto mais rápido.

3. **Retenção**
   - Renovação automática para cartões ativos.
   - Campanhas de reengajamento personalizadas para bloqueados/inativos.

4. **Monitoramento**
   - Dashboard contínuo com métricas QMR, taxas de bloqueio e expiração.

5. **Churn**
   - Analisar fatores de abandono pós-bloqueio.
   - Desenvolver modelos preditivos para retenção.

---

## 📂 Estrutura do Projeto

├── data/ # Dados brutos
├── notebooks/ # Notebooks de análise (EDA, métricas, gráficos)
├── outputs/ # Gráficos e tabelas gerados
├── README.md # Documentação do projeto


## 🚀 Tecnologias Utilizadas

- Python (Pandas, Numpy, Matplotlib, Seaborn)
- Jupyter Notebook
- Git/GitHub para versionamento
