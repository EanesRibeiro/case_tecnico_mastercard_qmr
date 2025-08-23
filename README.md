# 📊 Case Técnico: Análise e Otimização da Base de Cartões (QMR)

## 🎯 Objetivo

Automatizar o processo de relatórios trimestrais QMR e extrair insights estratégicos a partir dos dados transacionais para otimizar a base de cartões da Flash, identificando oportunidades de crescimento, migração de tecnologia e recuperação de receita.

## 💰 Principais Resultados Estratégicos

* **R$ 9,6 milhões/trimestre** identificados em receita potencial perdida devido a cartões bloqueados, justificando a criação de fluxos de reativação.
* **Top 10 empresas** mapeadas, concentrando mais de 3.500 cartões PIN, representando um alvo claro para campanhas de migração B2B.
* **25.267 cartões** com expiração no Q4/2023 segmentados por status (ativo/inativo) para direcionar ações de renovação e reengajamento.
* **100%** de automação no cálculo das métricas QMR, eliminando processos manuais e garantindo consistência.

## 🛠️ Tecnologias Utilizadas

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2C2D72?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3776AB?style=for-the-badge&logo=matplotlib&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-3776AB?style=for-the-badge&logo=seaborn&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)

## 📈 Principais Visualizações do Projeto

#### Atividade Transacional por Dia e Hora
O heatmap revela padrões de uso distintos entre dias úteis e fins de semana, com picos claros no horário de almoço e no final da tarde, fornecendo insumos para campanhas de marketing direcionadas.

![Heatmap de Atividade Transacional](outputs/transaction_activity_heatmap.png)

#### Evolução de Novos Cartões vs. Encerrados
O gráfico mostra um crescimento consistente na aquisição de novos cartões, mas também um aumento preocupante nos encerramentos. A projeção para o Q4 indica a manutenção dessa tendência, reforçando a necessidade de ações de retenção.

![Evolução de Novos Cartões vs. Encerrados](outputs/evolucao_new_vs_terminated.png)

## 📁 Estrutura do Projeto
case_tecnico_mastercard_qmr/
├── data/
│   ├── cards.csv
│   ├── cards_status.csv
│   └── cards_transactions.csv
├── notebooks/
│   └── EDA.ipynb
├── outputs/
│   ├── transaction_activity_heatmap.png
│   └── evolucao_new_vs_terminated.png
├── requirements.txt
└── README.md

## 🔧 Configuração do Ambiente

(A sua seção de configuração está ótima e pode ser mantida como no original)

## 📊 Metodologia

A análise foi conduzida em três etapas principais:

### 1. Exploração e Limpeza dos Dados (EDA)
* **Carregamento:** Ingestão de 3 tabelas principais (`cards`, `cards_status`, `cards_transactions`).
* **Validação:** Verificação de integridade referencial, duplicatas, valores nulos e consistência temporal.
* **Transformação:** Conversão de colunas de data para `datetime` com fuso horário (UTC) e padronização de tipos de dados.
* **Otimização de Performance:** Implementação da função vetorizada `get_status_on_date_vectorized` para processar snapshots de status de milhões de registros de forma eficiente, evitando loops e garantindo escalabilidade.

### 2. Construção das Métricas QMR
* Cálculo das métricas de fluxo da base de cartões: Início/Fim do trimestre, Novos, e Encerrados.
* Contagem de cartões únicos com transações por período.
* Validação da equação de balanço: `Fim ≈ Início + Novos - Encerrados` para garantir a consistência dos dados.

### 3. Análises Estratégicas
* Análise da penetração da tecnologia **Contactless vs. PIN**, com segmentação por empresa para identificar alvos de migração.
* Estudo do impacto de **cartões bloqueados**, estimando a perda de receita potencial.
* Mapeamento de **cartões expirando** no próximo trimestre para planejar ações de renovação e reengajamento.

## 🔑 Função-Chave de Performance

### `get_status_on_date_vectorized(status_df, ref_date)`
Esta função é o núcleo técnico do projeto. Ela determina o status mais recente de **todos** os cartões em uma data de referência de forma otimizada.

* **Abordagem:** Utiliza operações vetorizadas do Pandas, que são ordens de magnitude mais rápidas do que um loop `for` ou a aplicação de funções linha a linha (`.apply`).
* **Impacto:** Permite que o cálculo das métricas QMR, que exige múltiplas "fotografias" da base de cartões, seja executado em segundos, em vez de horas.

**Parâmetros:**
* `status_df` (DataFrame): O DataFrame `cards_status` com o histórico.
* `ref_date` (datetime): A data de referência para a consulta.

**Retorna:**
* `DataFrame`: Um DataFrame contendo o último status conhecido de cada cartão na data de referência.

## 🚀 Próximos Passos e Melhorias Futuras

(A sua seção atual está ótima e pode ser mantida como no original)

---

## 📞 Contato

**Desenvolvido por:** Eanes Ribeiro
**LinkedIn:** [linkedin.com/in/eanes-ribeiro](https://linkedin.com/in/eanes-ribeiro)
**GitHub:** [@EanesRibeiro](https://github.com/EanesRibeiro)

## 📄 Licença

Este projeto foi desenvolvido como case técnico para processo seletivo. Todos os dados são fictícios e utilizados apenas para fins educacionais.