# 📊 Case Técnico: Mastercard Quarterly Management Reporting (QMR)

## 🎯 Objetivo

Automatizar o processo de relatórios trimestrais QMR da Mastercard e extrair insights estratégicos para otimização da base de cartões da Flash, identificando oportunidades de crescimento e recuperação de receita.

## 💰 Principais Resultados

- **R$ 9,6 milhões** identificados em receita perdida por cartões bloqueados
- **25.267 cartões** expirando Q4/2023 mapeados para renovação
- **79.8%** de penetração contactless vs 20.2% PIN
- **100%** automação do processo QMR implementada

## 📁 Estrutura do Projeto

```
case_tecnico_mastercard_qmr/
├── data/                          # Dados brutos (não versionados)
│   ├── cards.csv
│   ├── cards_status.csv
│   └── cards_transactions.csv
├── notebooks/                     # Análises e exploração
│   └── EDA.ipynb                 # Notebook principal com todas as análises
├── outputs/                       # Resultados gerados
│   ├── graficos/                 # Visualizações exportadas
│   └── tabelas/                  # Métricas QMR consolidadas
├── requirements.txt              # Dependências do projeto
├── README.md                     # Documentação do projeto
└── .gitignore                    # Arquivos ignorados pelo Git
```

## 🔧 Configuração do Ambiente

### Pré-requisitos
- Python 3.8+
- Jupyter Notebook/Lab
- Git

### Instalação

1. **Clone o repositório:**
```bash
git clone https://github.com/EanesRibeiro/case_tecnico_mastercard_qmr.git
cd case_tecnico_mastercard_qmr
```

2. **Crie um ambiente virtual:**
```bash
python -m venv venv
source venv/bin/activate  # Linux/Mac
# ou
venv\Scripts\activate     # Windows
```

3. **Instale as dependências:**
```bash
pip install -r requirements.txt
```

4. **Baixe os dados:**
   - Acesse: [Google Drive - Dados do Projeto](https://drive.google.com/drive/folders/1T3VXMs0XWnuV59n0puhRTXXlfyDwqwvO)
   - Baixe os arquivos CSV para a pasta `data/`

5. **Execute o notebook:**
```bash
jupyter notebook notebooks/EDA.ipynb
```

## 📊 Metodologia

### 1. Exploração e Limpeza dos Dados (EDA)
- **Carregamento:** 3 tabelas principais (cards, cards_status, cards_transactions)
- **Validação:** Verificação de duplicatas, valores nulos e consistência temporal
- **Transformação:** Conversão de colunas de data para datetime
- **Função customizada:** `get_status_on_date(card_number, ref_date)` para determinar status histórico

### 2. Construção das Métricas QMR
- Cards at Beginning/End of Quarter (Open/Blocked)
- New Cards Obtained During Quarter
- Cards Terminated During Quarter  
- Cards with at Least One Transaction
- Validação da equação: `End ≈ Beginning + New - Terminated`

### 3. Análises Estratégicas
- **Penetração Contactless vs PIN** por empresa e segmento
- **Análise de bloqueios** e tempo médio de resolução
- **Cartões expirando** e oportunidades de renovação
- **Segmentação de clientes** para campanhas direcionadas

## 📈 Principais Insights

### Crescimento da Base
- **Q1→Q3 2023:** Crescimento de 61% (159.767 → 258.007 cartões)
- **Padrão preocupante:** Terminações cresceram 136% no período
- **Taxa de transação:** Melhoria consistente (126K → 173K cartões ativos)

### Tecnologia Contactless
| Tecnologia | Quantidade | Percentual |
|------------|------------|------------|
| Contactless | 205.892 | 79.8% |
| PIN | 52.115 | 20.2% |

**Concentração PIN:** Top 10 empresas possuem 3.500+ cartões PIN (oportunidade direcionada)

### Cartões Bloqueados
- **6.092 cartões** bloqueados no fim Q3/2023
- **R$ 9,6 milhões/trimestre** em receita perdida estimada
- **36.217 eventos** de bloqueio sem resolução identificados

## 🎯 Recomendações Estratégicas

### 1. Gestão de Bloqueios
- **Sistema de alertas** escalonados (30/60/90 dias)
- **Campanhas de reativação** automatizadas
- **Processo simplificado** de desbloqueio via app

### 2. Migração Contactless
- **Foco B2B:** Campanha direcionada às top 10 empresas
- **Renovação inteligente:** Upgrade automático PIN→Contactless
- **Meta:** 85%+ penetração contactless até Q4/2023

### 3. Gestão de Expiração
- **21.592 ativos:** Renovação automática prioritária
- **3.673 inativos:** Campanha reengajamento com incentivos

## 🔍 Principais Funções

### `get_status_on_date(card_number, ref_date)`
Determina o status de um cartão em uma data específica baseado no histórico de mudanças.

**Parâmetros:**
- `card_number` (str): Número do cartão
- `ref_date` (datetime): Data de referência

**Retorna:**
- `str`: Status do cartão na data ('OPEN', 'TEMPORARILY_BLOCKED', etc.)

**Exemplo:**
```python
status = get_status_on_date('1234567890', pd.to_datetime('2023-09-30'))
print(status)  # 'OPEN'
```

## 📊 Visualizações Disponíveis

- **Evolução QMR:** Gráficos de linha com métricas trimestrais
- **Contactless vs PIN:** Pizza chart + análise por empresa
- **Timeline de bloqueios:** Distribuição temporal
- **Pipeline expiração:** Segmentação por status

## 🚀 Próximos Passos

### Implementação (Roadmap)
- **Semana 1-2:** Dashboard QMR automatizado
- **Semana 3-4:** Sistema de alertas de bloqueio
- **Mês 2:** Campanha migração contactless B2B
- **Mês 3:** Política renovação automática

### Melhorias Futuras
- [ ] Dashboard interativo (Streamlit/Dash)
- [ ] Modelo preditivo de bloqueios
- [ ] API para consulta de métricas em tempo real
- [ ] Integração com sistemas internos da Flash

## 📋 Dependências Principais

```txt
pandas>=1.3.0
numpy>=1.21.0
matplotlib>=3.4.0
seaborn>=0.11.0
jupyter>=1.0.0
openpyxl>=3.0.0
```

## 📞 Contato

**Desenvolvido por:** Eanes Ribeiro  
**LinkedIn:** [linkedin.com/in/eanes-ribeiro](https://linkedin.com/in/eanes-ribeiro)  
**GitHub:** [@EanesRibeiro](https://github.com/EanesRibeiro)  
**Email:** eanes.ribeiro@email.com

## 📄 Licença

Este projeto foi desenvolvido como case técnico para processo seletivo. Todos os dados são fictícios e utilizados apenas para fins educacionais.

---

⭐ **Se este projeto foi útil, deixe uma estrela no repositório!**