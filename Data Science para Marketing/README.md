# 📊 Data Science aplicado para o Marketing

Repositório de estudos do curso **Data Science para Marketing** (Alura), com anotações práticas em Python aplicadas. O notebook reúne exercícios de análise exploratória, estatística descritiva e visualização de dados usando **Pandas**, **Seaborn**, **Matplotlib** e **Numpy**, com foco em métricas de campanhas (CTR, ROI, receita, custo) e dados de vendas.

> 📁 Arquivo principal: `Analisando e Explorando Dados.ipynb`

---

## 🗂️ Estrutura das Aulas

| Aula | Tema | Foco principal |
|------|------|-----------------|
| [1](#-aula-1---conhecendo-os-dados) | Conhecendo os Dados | Primeiros contatos com o dataset, métricas básicas (CTR) |
| [2](#-aula-2---analisando-os-dados) | Analisando os Dados | Filtros, segmentação (`query`, `groupby`) e distribuições |
| [3](#-aula-3---entendendo-os-tipos-de-variáveis) | Entendendo os Tipos de Variáveis | Tipos de dados, variáveis numéricas e categóricas |
| [4](#-aula-4---visualizando-os-dados) | Visualizando os Dados | Gráficos de barras, setor e contagem categórica |
| [5](#-aula-5---estatística-dos-dados) | Estatística dos Dados | Medidas de tendência central, dispersão e ROI |

---

## 📘 Aula 1 - Conhecendo os Dados

Primeiro contato com o dataset de campanhas (`campanha.csv`), com foco em **carregar, inspecionar e explorar** as colunas disponíveis.

**Funcionalidades aprendidas:**
- Importação das bibliotecas padrão: `pandas` e `seaborn`
- Leitura de arquivos CSV com `pd.read_csv()`
- `.shape` → dimensões do dataframe (linhas x colunas)
- `.head()` → visualização das primeiras linhas
- Seleção de colunas específicas (`df['coluna']`)
- `.unique()` → valores únicos de uma coluna (ex: canais de marketing)
- `.value_counts()` → contagem de ocorrências por categoria
- Criação de **métrica derivada**: **CTR (Click-Through Rate)**
  ```python
  campanha['ctr'] = (campanha['cliques'] / campanha['impressoes']) * 100
  ```
- `.describe()` → panorama estatístico (média, mediana, desvio padrão, mín/máx)
- Visualização com **boxplot** (`sns.boxplot()`) para identificar distribuição e outliers do CTR

🎯 **Aplicação para Trading/Marketing:** primeiro passo de qualquer análise de performance de mídia — entender a granularidade dos dados e calcular indicadores-chave (KPIs) como o CTR.

---

## 📗 Aula 2 - Analisando os Dados

Aprofundamento em **filtros, segmentações e visualização de distribuições**, explorando tanto a base de campanhas quanto uma base de vendas (`vendas_zoop.csv`).

**Funcionalidades aprendidas:**
- `.query()` → filtragem de dados com sintaxe semelhante a SQL
  ```python
  campanha.query('Id_campanha == 1').mean(numeric_only=True)
  ```
- Cálculo de médias filtradas por campanha/coluna específica
- `.groupby()` → análises segmentadas (ex: média de impressões por campanha, CTR médio por canal)
- Visualização de agregações com `.plot(kind='hist')`
- `sns.displot()` → histogramas de distribuição, com parâmetro `kde=True` para suavizar a curva de densidade
- Combinação de **Seaborn + Matplotlib** para customizar título e exibição (`plt.title()`, `plt.show()`)
- Análise cruzada de variáveis categóricas com `hue` (ex: Categoria do Produto x Região, Categoria do Produto x Gênero)

🎯 **Aplicação para Trading/Marketing:** segmentação é essencial para comparar performance entre canais, campanhas e perfis de clientes, identificando padrões de comportamento de compra.

---

## 📙 Aula 3 - Entendendo os Tipos de Variáveis

Foco em entender o **comportamento estatístico** de variáveis-chave do negócio (receita e custo) e os **tipos de dados** presentes no dataset.

**Funcionalidades aprendidas:**
- Análise de distribuição da **Receita** e do **Custo** das campanhas via `sns.displot()`
- `.info()` → identificação dos tipos de dados de cada coluna (int, float, object)
- Diferenciação entre **variáveis numéricas** (contínuas/discretas) e **variáveis categóricas**
- Reutilização de `.unique()` e `.value_counts()` para inspecionar variáveis categóricas (ex: estado)

🎯 **Aplicação para Trading/Marketing:** entender se uma variável é numérica ou categórica define qual tipo de análise estatística e gráfico é adequado — fundamental antes de qualquer modelagem ou cruzamento de dados.

---

## 📕 Aula 4 - Visualizando os Dados

Aula com maior volume de conteúdo, dedicada a **gráficos para variáveis categóricas** e técnicas de manipulação de dados para deixá-los "prontos para plotagem".

**Funcionalidades aprendidas:**
- `.value_counts()` retornando índice (categoria) e valores (contagem)
- Conversão de `value_counts()` em DataFrame com `.to_frame()` e `.reset_index()`
- Renomeação de colunas com `.columns = [...]`
- `.plot()` genérico vs. gráfico de **barras** (`sns.barplot()`) — escolha do gráfico certo para o tipo de dado
- `sns.countplot()` → contagem direta de categorias sem necessidade de agregação manual
- **Gráfico de Setores (Pizza)** com `.plot(kind='pie')`
- Criação de dicionários e DataFrames customizados para simplificar visualizações (ex: agrupar "SP" vs. "Outros estados")
- Combinação de `.query()` com `sns.countplot()` para refinar visualizações (ex: excluir SP e analisar o restante)

🎯 **Aplicação para Trading/Marketing:** escolher a visualização certa (barras, pizza, contagem) é o que transforma dado bruto em **insight de negócio** apresentável para stakeholders — essencial em relatórios de performance e dashboards.

---

## 📓 Aula 5 - Estatística dos Dados

Aula final com foco em **estatística aplicada à tomada de decisão**, introduzindo o cálculo de uma das métricas mais importantes do Trading/Marketing: o **ROI**.

**Funcionalidades aprendidas:**
- Importação da biblioteca `numpy` para cálculos estatísticos
- Criação da métrica **ROI (Return Over Investment)**:
  ```python
  campanha['roi'] = (campanha['receita'] - campanha['custo']) / campanha['custo']
  ```
- Visualização da distribuição geral do ROI com `sns.displot()`
- Filtragem por canal (`Google Ads`, `Email`) usando `.query()` para comparar performance
- Cálculo de média de ROI por canal com `.mean()`
- **Medidas de Tendência Central** (média) e **Medida de Dispersão** (desvio padrão) com `np.mean()` e `np.std()`
- Demonstração prática de por que **a média isolada pode enganar**: dois canais com a mesma média podem ter desvios padrão completamente diferentes, indicando níveis de risco/instabilidade distintos

🎯 **Aplicação para Trading/Marketing:** o ROI é a métrica central para decisões de investimento em canais de mídia. Entender a dispersão (desvio padrão) além da média evita decisões equivocadas — um canal "estável" pode ser mais seguro que outro com a mesma média, porém mais volátil.

---

## 🛠️ Stack Técnica Utilizada

| Biblioteca | Uso principal |
|------------|----------------|
| **Pandas** | Leitura, manipulação e agregação de dados (`read_csv`, `groupby`, `query`, `value_counts`, , `sum`) |
| **Seaborn** | Visualizações estatísticas (`boxplot`, `displot`, `barplot`, `countplot`) |
| **Matplotlib** | Customização de gráficos (`title`, `show`) |
| **NumPy** | Cálculos estatísticos (`mean`, `std`) |

---

## 📌 Principais Métricas Calculadas

- **CTR (Click-Through Rate):** `cliques / impressões * 100`
- **ROI (Return Over Investment):** `(receita - custo) / custo`
- **Medidas de Tendência Central:** média, mediana, moda
- **Medidas de Dispersão:** desvio padrão

---

## 🚀 Próximos Passos de Estudo

- [ ] Aplicar testes de hipótese para comparação entre canais
- [ ] Explorar correlação entre variáveis (ex: custo x receita)
- [ ] Avançar para modelos preditivos de performance de campanha
- [ ] Construir dashboards interativos (Power BI / Looker Studio) a partir das análises

---

*Repositório de estudos pessoais — curso Data Science para Marketing (Alura).*
