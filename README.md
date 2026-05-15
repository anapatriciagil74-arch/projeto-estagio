# 🎓 Projeto de Estágio - AutoML & Data Processing

> Exploração de técnicas AutoML com processamento avançado de dados para classificação e análise preditiva

[![Python](https://img.shields.io/badge/Python-3.13.9-blue?logo=python&logoColor=white)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)](https://jupyter.org/)
[![Pandas](https://img.shields.io/badge/Pandas-Latest-green?logo=pandas)](https://pandas.pydata.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-Latest-blue?logo=scikit-learn)](https://scikit-learn.org/)
[![License](https://img.shields.io/badge/License-Academic-lightgrey)](LICENSE)

---

## 📌 Informações do Projeto

| Campo | Detalhes |
|-------|----------|
| **Instituição** | Licenciatura em Inteligência Artificial e Ciências de Dados |
| **Período** | 2025/2026 |
| **Autor** | Ana Patrícia Gil |
| **Status** | ✅ Em Desenvolvimento Activo |
| **Última Atualização** | 15 de maio de 2026 |

---

## 🎯 Objetivos do Projeto

Este projeto de estágio tem como foco principal:

1. **Exploração de Dados**
   - Análise de múltiplos datasets públicos
   - Identificação de padrões e anomalias
   - Caracterização de distribuições

2. **Processamento e Limpeza**
   - Tratamento de valores ausentes
   - Normalização e standardização
   - Feature engineering e seleção

3. **Modelagem AutoML**
   - Comparação de algoritmos de aprendizagem
   - Otimização automática de hiperparâmetros
   - Validação cruzada e avaliação

4. **Integração Cloud**
   - Deployment em Azure/Vertex AI
   - Reproducibilidade e versionamento
   - Documentação técnica

---

## 📂 Estrutura do Repositório

```
projeto-estagio/
│
├── 📓 Untitled.ipynb                    # Notebook principal - Pipeline completo
├── 📄 README.md                         # Este ficheiro
├── 📊 Relatório.docx                    # Relatório académico de estágio
│
├── 📂 Datasets/
│   ├── adults.csv                       # Dataset bruto (30K+ registos)
│   ├── adults_data.csv                  # Dataset processado
│   ├── data_clean_final.csv             # Dataset final validado
│   └── iris.data                        # Dataset Iris (150 amostras)
│
├── 📂 azure/                            # Configurações cloud
│   └── [...ficheiros de configuração]
│
├── 📂 open source iris/                 # Análise exploratória
│   └── [Notebooks e visualizações]
│
└── 📂 open source breast cancer/        # Análise exploratória
    └── [Notebooks e análises]
```

---

## 🗂️ Datasets Utilizados

### 1. Adults Dataset 👥
**Previsão de Renda (Classificação Binária)**

| Propriedade | Valor |
|-------------|-------|
| **Fonte** | UCI Machine Learning Repository |
| **Registos** | 30.162 (após limpeza) |
| **Atributos** | 15 features + target |
| **Target** | `income` (≤50K ou >50K) |
| **Features** | Idade, educação, profissão, horas/semana, etc. |
| **Status** | ✅ Processado e validado |

**Processamento Aplicado:**
- ✅ Remoção de 2.399 registos com valores ausentes
- ✅ Normalização de nomes de colunas (lowercase, sem hífens)
- ✅ Tratamento de valores especiais (`?` → `Unknown`)
- ✅ Validação de qualidade (0 NaN)

### 2. Iris Dataset 🌸
**Classificação de Espécies (Multi-classe)**

| Propriedade | Valor |
|-------------|-------|
| **Fonte** | Ronald Fisher (Clássico ML) |
| **Amostras** | 150 |
| **Features** | 4 (comprimento/largura sépalas e pétalas) |
| **Classes** | 3 (Setosa, Versicolor, Virginica) |
| **Status** | ✅ Análise exploratória completa |

### 3. Breast Cancer Dataset 🏥
**Diagnóstico Benigno/Maligno (Classificação Binária)**

| Propriedade | Valor |
|-------------|-------|
| **Localização** | Pasta `open source breast cancer/` |
| **Objetivo** | Previsão de diagnóstico |
| **Status** | ✅ Em análise |

---

## 🛠️ Setup & Instalação

### Pré-requisitos
- Python 3.13.9 ou superior
- pip (gestor de pacotes Python)
- Git

### Passo 1: Clonar Repositório

```bash
git clone https://github.com/anapatriciagil74-arch/projeto-estagio.git
cd projeto-estagio
```

### Passo 2: Criar Ambiente Virtual (Recomendado)

```bash
# macOS/Linux
python3 -m venv venv
source venv/bin/activate

# Windows
python -m venv venv
venv\Scripts\activate
```

### Passo 3: Instalar Dependências

```bash
pip install --upgrade pip
pip install jupyter pandas numpy scikit-learn matplotlib seaborn azure-sdk plotly
```

### Passo 4: Iniciar Jupyter Notebook

```bash
jupyter notebook
```

Abra `Untitled.ipynb` no browser que se abre automaticamente.

---

## 📊 Pipeline de Processamento de Dados

O notebook principal executa um pipeline completo de tratamento:

### 1️⃣ **Carregamento Seguro**
```python
df = pd.read_csv('Datasets/adults.csv', dtype_backend='numpy_nullable')
```

### 2️⃣ **Exploração Inicial**
- Visualização de primeiras linhas
- Análise de tipos de dados
- Identificação de valores ausentes
- Estatísticas descritivas

### 3️⃣ **Normalização de Estrutura**
```python
# Limpeza de nomes de colunas
df.columns = df.columns.str.strip().str.lower().str.replace('-', '_')
```

### 4️⃣ **Tratamento de Valores Ausentes**
- Substituição de `?` por `Unknown`
- Remoção de linhas com NaN
- Análise de distribuição

### 5️⃣ **Validação de Qualidade**
```python
# Verificações finais
assert df.isnull().sum().sum() == 0, "Dados contêm NaN!"
print(f"✅ Dataset validado: {df.shape}")
```

### 6️⃣ **Exportação**
```python
df.to_csv('Datasets/data_clean_final.csv', index=False)
```

---

## 📈 Resultados & Validação

### Adults Dataset - Transformação

| Métrica | Antes | Depois | Status |
|---------|-------|--------|--------|
| Registos | 32.561 | 30.162 | -7.4% (limpeza) |
| Atributos | 15 | 15 | ✅ Mantidos |
| Valores Nulos | 2.399+ | 0 | ✅ Eliminados |
| Caracteres Inválidos | Sim | Não | ✅ Normalizados |
| Pronto para ML | ❌ Não | ✅ Sim | ✅ Validado |

### Checklist de Qualidade ✅

```
✅ Shape final: (30.162, 15)
✅ Valores nulos: 0
✅ Variável target presente: income
✅ Classes balanceadas: Analisadas
✅ Features numéricas: Validadas
✅ Features categóricas: Tratadas
✅ Compatível com Vertex AI: Sim
✅ Compatível com Azure ML: Sim
```

---

## 🤖 Técnicas de ML Utilizadas

### Algoritmos Testados
- 📊 **Regressão Logística** (baseline)
- 🌳 **Random Forest** (ensemble)
- 🎯 **Gradient Boosting** (XGBoost/LightGBM)
- 🧠 **Neural Networks** (quando aplicável)

### Validação & Avaliação
- **Validação Cruzada**: k-fold (k=5)
- **Métricas**: Accuracy, Precision, Recall, F1-Score, AUC-ROC
- **Otimização**: Grid Search / Random Search

---

## ☁️ Integração Cloud

### Microsoft Azure

**Recursos Configurados:**
- 🔐 Azure Storage (dados)
- 🤖 Azure Machine Learning (modelagem)
- 📊 Vertex AI (AutoML - experimental)

**Ficheiros de Configuração:**
- Credenciais: `azure/config/`
- Pipelines: `azure/pipelines/`
- Modelos: `azure/models/`

### Como Usar

```python
# Exemplo: Autenticação Azure
from azure.identity import DefaultAzureCredential
from azure.ai.ml import MLClient

credential = DefaultAzureCredential()
ml_client = MLClient(credential, subscription_id, resource_group, workspace_name)
```

---

## 📝 Análises Incluídas

### 📊 Exploratory Data Analysis (EDA)
- Distribuições univariadas
- Correlações entre variáveis
- Detecção de outliers (IQR, Z-score)
- Análise de balanceamento de classes
- Visualizações (histogramas, scatter plots, box plots)

### 🧹 Data Cleaning
- Imputação de missing values
- Tratamento de outliers
- Normalização (Min-Max, Z-score)
- Encoding de variáveis categóricas
- Feature scaling

### 📈 Feature Engineering
- Seleção de features (correlação, importância)
- Criação de novas features
- Redução dimensional (PCA)

### 🎯 Model Evaluation
- Matriz de confusão
- Curvas ROC-AUC
- Learning curves
- Hyperparameter tuning

---

## 📚 Documentação Complementar

### 📄 Relatório Académico
**`Relatório.docx`** contém:
- Contexto e motivação do projeto
- Metodologia detalhada
- Análise de resultados
- Conclusões e trabalho futuro
- Referências bibliográficas

### 📖 Guias Externos Úteis

| Recurso | URL | Tópico |
|---------|-----|--------|
| Pandas Docs | [pandas.pydata.org](https://pandas.pydata.org) | Manipulação de dados |
| Scikit-learn | [scikit-learn.org](https://scikit-learn.org) | Machine Learning |
| UCI ML Repository | [archive.ics.uci.edu](https://archive.ics.uci.edu) | Datasets públicos |
| Azure ML | [azure.microsoft.com/ml](https://azure.microsoft.com/en-us/services/machine-learning/) | Cloud ML |

---

## 🚀 Quick Start (5 Minutos)

```bash
# 1. Clone
git clone https://github.com/anapatriciagil74-arch/projeto-estagio.git && cd projeto-estagio

# 2. Virtual Environment
python -m venv venv && source venv/bin/activate

# 3. Dependências
pip install jupyter pandas numpy scikit-learn matplotlib seaborn azure-sdk plotly

# 4. Jupyter
jupyter notebook

# 5. Abra Untitled.ipynb e execute
# Kernel → Restart & Run All
```

**Output esperado:**
- ✅ `adults_data.csv` - Dataset processado
- ✅ `data_clean_final.csv` - Dataset final
- ✅ Gráficos de EDA
- ✅ Métricas de modelos

---

## 💡 Exemplos de Uso

### Carregar Dataset Processado

```python
import pandas as pd

df = pd.read_csv('Datasets/data_clean_final.csv')
print(df.head())
print(df.info())
```

### Treinar Modelo Simples

```python
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score, classification_report

# Preparação
X = df.drop('income', axis=1)
y = df['income']

# Encode categóricos se necessário
X_encoded = pd.get_dummies(X, drop_first=True)

# Split
X_train, X_test, y_train, y_test = train_test_split(
    X_encoded, y, test_size=0.2, random_state=42
)

# Modelo
model = RandomForestClassifier(n_estimators=100, random_state=42)
model.fit(X_train, y_train)

# Avaliação
y_pred = model.predict(X_test)
print(f"Accuracy: {accuracy_score(y_test, y_pred):.4f}")
print(classification_report(y_test, y_pred))
```

---

## ✅ Checklist de Desenvolvimento

- ✅ Carregamento de datasets múltiplos
- ✅ Exploração e análise inicial (EDA)
- ✅ Limpeza e preprocessamento
- ✅ Tratamento de valores ausentes
- ✅ Normalização de estrutura de dados
- ✅ Validação de qualidade
- ✅ Exportação em formatos standard
- ✅ Integração com Azure
- ✅ Documentação completa
- ⏳ Implantação em produção (futuro)

---

## 🔧 Troubleshooting

### Erro: `ModuleNotFoundError: No module named 'pandas'`
```bash
pip install pandas
```

### Erro: `FileNotFoundError: Datasets/adults.csv`
```bash
# Certifique-se que está no diretório raiz do projeto
# e que os ficheiros de dados existem
ls Datasets/
```

### Erro: Jupyter não abre
```bash
# Reinstale jupyter
pip uninstall jupyter -y && pip install jupyter
jupyter notebook
```

### Performance Lenta
- Use `pandas` com `dtype_backend='numpy_nullable'`
- Considere amostras menores para testes rápidos
- Implemente cache de processamento

---

## 📋 Informações Técnicas

### Ambiente Recomendado

| Componente | Especificação |
|-----------|---------------|
| **Python** | 3.13.9+ |
| **RAM** | 8GB+ (mínimo 4GB) |
| **Disco** | 2GB+ |
| **SO** | Windows 10+, macOS 10.14+, Linux (qualquer) |

### Stack de Tecnologias

| Tecnologia | Versão | Uso |
|-----------|--------|-----|
| Python | 3.13.9 | Linguagem principal |
| Jupyter | Latest | Análise interativa |
| Pandas | Latest | Manipulação de dados |
| NumPy | Latest | Computação numérica |
| scikit-learn | Latest | Machine Learning |
| Matplotlib/Seaborn | Latest | Visualizações |
| Azure SDK | Latest | Integração cloud |

---

## 📞 Contacto & Suporte

**Autor:** Ana Patrícia Gil

| Canal | Link |
|-------|------|
| 🔗 GitHub | [@anapatriciagil74-arch](https://github.com/anapatriciagil74-arch) |
| 📧 Email | Disponível no perfil GitHub |
| 🏫 Instituição | Licenciatura em IA e Ciências de Dados |

---

## 📜 Licença

Este projeto é desenvolvido como **trabalho académico de estágio**.

⚠️ **Uso restrito a fins educacionais e académicos**. A reutilização ou publicação requer autorização do autor.

---

## 📝 Notas Importantes

> ⚠️ **Dados Sensíveis**: O dataset Adults contém dados demográficos reais. Usar com responsabilidade e conformidade GDPR.

> 💡 **Reproducibilidade**: Todos os scripts usam `random_state` fixo (42) para garantir reproducibilidade dos resultados.

> 🔄 **Versionamento**: Utilize Git para controlo de versões. Não commit de datasets brutos muito grandes.

> 📊 **Performance**: Para datasets > 100MB, considere usar `Dask` ou `Polars` ao invés de Pandas.

---

## 🗓️ Histórico de Versões

| Versão | Data | Alterações |
|--------|------|-----------|
| 1.0 | 14/05/2026 | Release inicial |
| 1.1 | 14/05/2026 | README expandido e refatorizado |
| 1.2 | 15/05/2026 | Melhorias de estrutura e documentação |

---

<div align="center">

**Desenvolvido com ❤️ como projeto de estágio**

*Última atualização: 15 de maio de 2026*

[⬆ Voltar ao Topo](#-projeto-de-estágio---automl--data-processing)

</div>
