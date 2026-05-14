# 🎓 Projeto de Estágio - AutoML e Processamento de Dados

> Exploração e testes de técnicas de AutoML com processamento avançado de dados

**Instituição**: Licenciatura em Inteligência Artificial e Ciências de Dados  
**Período**: 2025/2026  
**Autor**: Ana Patrícia Gil

---

## 📖 Visão Geral

Este repositório contém o desenvolvimento completo de um projeto de estágio focado em:
- ✅ Exploração e análise de datasets públicos
- ✅ Técnicas avançadas de limpeza e preprocessamento de dados
- ✅ Implementação e teste de modelos AutoML
- ✅ Integração com plataformas cloud (Azure/Vertex AI)
- ✅ Documentação e relatório académico

O projeto utiliza **Python**, **Jupyter Notebooks** e ferramentas de machine learning para processar múltiplos datasets e validar técnicas de automação de modelos.

---

## 📁 Estrutura do Projeto

```
projeto-estagio/
│
├── 📓 Untitled.ipynb                          # Notebook principal - Processamento de dados
├── 📄 README.md                               # Este ficheiro
├── 📊 Modelo 2025_26 Relatório de Estágio... # Relatório académico (Word)
│
├── 📂 Datasets/
│   ├── adults.csv                             # Dataset bruto - Dados demográficos
│   ├── adults_data.csv                        # Dataset processado - Adults
│   ├── data_clean_final.csv                   # Dataset final limpo
│   └── iris.data                              # Dataset Iris (classificação)
│
├── 📂 azure/                                  # Integração com Azure
│   └── [Ficheiros de configuração cloud]
│
├── 📂 open source iris/                       # Análise exploradora - Iris
│   └── [Notebooks e análises]
│
└── 📂 open source breast cancer/              # Análise exploradora - Breast Cancer
    └── [Notebooks e análises]
```

---

## 🛠️ Tecnologias e Dependências

| Tecnologia | Versão | Propósito |
|-----------|--------|----------|
| **Python** | 3.13.9 | Linguagem principal |
| **Jupyter Notebook** | Latest | Análise interativa |
| **Pandas** | Latest | Manipulação de dados |
| **NumPy** | Latest | Computação numérica |
| **Scikit-learn** | Latest | Machine Learning |
| **Azure SDK** | Latest | Integração cloud |

### Instalação de Dependências

```bash
# Criar ambiente virtual (recomendado)
python -m venv venv
source venv/bin/activate  # macOS/Linux
# ou
venv\Scripts\activate  # Windows

# Instalar dependências
pip install jupyter pandas numpy scikit-learn azure-sdk matplotlib seaborn
```

---

## 📊 Datasets Utilizados

### 1️⃣ **Adults Dataset**
- **Fonte**: Censo dos EUA (UCI Machine Learning Repository)
- **Arquivo**: `adults.csv`
- **Dimensões**: 30.162 registos × 15 atributos
- **Objetivo**: Previsão de renda (≤50K ou >50K)
- **Atributos**: Idade, educação, profissão, horas de trabalho, etc.

**Status**: ✅ Processado e validado

### 2️⃣ **Iris Dataset**
- **Fonte**: Ronald Fisher (Clássico da ML)
- **Arquivo**: `iris.data`
- **Dimensões**: 150 amostras × 4 características
- **Objetivo**: Classificação de espécies de iris
- **Classes**: Setosa, Versicolor, Virginica

**Status**: ✅ Análise exploratória completa

### 3️⃣ **Breast Cancer Dataset**
- **Fonte**: Dataset público de diagnóstico
- **Localização**: `open source breast cancer/`
- **Objetivo**: Classificação benigno/maligno

**Status**: ✅ Em análise

---

## 🔧 Processamento de Dados

### Pipeline de Limpeza Implementado

O notebook `Untitled.ipynb` executa as seguintes etapas:

#### 1. **Carregamento Seguro**
```python
# Importação com tipagem correta
df = pd.read_csv('adults.csv', dtype_backend='numpy_nullable')
```

#### 2. **Normalização de Estrutura**
- ✅ Remoção de espaços em branco nos nomes de colunas
- ✅ Substituição de hífens por underscores (compatibilidade Vertex AI)
- ✅ Conversão para lowercase (padrão)

#### 3. **Tratamento de Valores Ausentes**
- ✅ Substituição de `?` por `Unknown`
- ✅ Remoção de linhas com NaN
- ✅ Análise de distribuição de missing values

#### 4. **Validação de Qualidade**
- ✅ Verificação de dimensionalidade
- ✅ Confirmar ausência de valores nulos (0 NaN)
- ✅ Identificar variável alvo

#### 5. **Exportação**
```python
# Dataset final validado
df.to_csv('data_clean_final.csv', index=False)
```

---

## 📈 Resultados do Processamento

### Adults Dataset - Antes vs Depois

| Métrica | Antes | Depois |
|---------|-------|--------|
| **Registos** | 32.561 | 30.162 |
| **Atributos** | 15 | 15 |
| **Valores Nulos** | 2.399+ | ✅ 0 |
| **Caracteres Especiais** | Sim (hífens) | ✅ Normalizados |
| **Pronto para ML** | ❌ Não | ✅ Sim |

### Validação Final
```
✅ Shape: (30162, 15)
✅ Valores Nulos: 0
✅ Variável Alvo: income ['<=50K', '>50K']
✅ Compatível com Azure Vertex AI
```

---

## 🚀 Como Utilizar

### Quick Start (5 minutos)

```bash
# 1. Clone o repositório
git clone https://github.com/anapatriciagil74-arch/projeto-estagio.git
cd projeto-estagio

# 2. Configure o ambiente
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 3. Inicie Jupyter
jupyter notebook

# 4. Abra Untitled.ipynb e execute as células
```

### Executar Processamento Completo

1. Abra `Untitled.ipynb` no Jupyter
2. Execute todas as células (Kernel → Restart & Run All)
3. Outputs gerados:
   - `adults_data.csv` - Dataset processado
   - `data_clean_final.csv` - Dataset final
   - Relatórios de qualidade no console

### Usar os Datasets Processados

```python
import pandas as pd

# Carregar dataset pronto para ML
df = pd.read_csv('data_clean_final.csv')

# Separar features e target
X = df.drop('income', axis=1)
y = df['income']

# Usar em modelo de ML
from sklearn.ensemble import RandomForestClassifier
model = RandomForestClassifier()
model.fit(X, y)
```

---

## ☁️ Integração Azure

O projeto inclui configuração para implantação em Microsoft Azure:

**Recursos Utilizados**:
- Azure Storage (armazenamento de dados)
- Azure Machine Learning (treino de modelos)
- Vertex AI (AutoML - quando aplicável)

**Ficheiros de Configuração**: Ver pasta `azure/`

---

## 📝 Documentação

### Relatório Académico
📄 **`Modelo 2025_26 Relatório de Estágio - Lic. em Engª Informática 2.docx`**

Contém:
- Análise completa do projeto
- Metodologia e técnicas aplicadas
- Resultados e conclusões
- Referências bibliográficas

---

## 📚 Análises Incluídas

### 📊 Exploratory Data Analysis (EDA)
- Distribuições de variáveis
- Correlações entre atributos
- Detecção de outliers
- Análise de balanceamento de classes

### 🧹 Data Cleaning
- Imputação de valores faltantes
- Normalização e standardização
- Tratamento de valores categóricos
- Feature engineering

### 🤖 AutoML Testing
- Comparação de algoritmos
- Validação cruzada
- Otimização de hiperparâmetros
- Avaliação de modelos

---

## 📋 Checklist de Desenvolvimento

- ✅ Carregamento e exploração de datasets
- ✅ Limpeza e preprocessamento de dados
- ✅ Tratamento de valores ausentes
- ✅ Normalização de estrutura
- ✅ Validação de qualidade
- ✅ Exportação para formatos standard
- ✅ Integração Azure
- ✅ Documentação e relatório
- ⏳ Implantação em produção (Em desenvolvimento)

---

## 🔗 Recursos Externos

| Recurso | Link |
|---------|------|
| UCI ML Repository | https://archive.ics.uci.edu |
| Scikit-learn | https://scikit-learn.org |
| Pandas Documentation | https://pandas.pydata.org |
| Azure ML | https://azure.microsoft.com/services/machine-learning |

---

## 👤 Autor & Contacto

**Ana Patrícia Gil**
- 🔗 GitHub: [@anapatriciagil74-arch](https://github.com/anapatriciagil74-arch)
- 📧 Email: Disponível no perfil GitHub
- 🏫 Instituição: Licenciatura em IA e Ciências de Dados

---

## 📄 Licença

Este projeto é desenvolvido como trabalho académico de estágio.  
Uso apenas para fins educacionais e académicos.

---

## 🗂️ Versionamento

| Versão | Data | Alterações |
|--------|------|-----------|
| 1.0 | 14/05/2026 | Release inicial do projeto |
| 1.1 | 14/05/2026 | README refactorizado e expandido |

---

## 📝 Notas Importantes

> ⚠️ **Dados Sensíveis**: O dataset Adults contém dados demográficos; usar com cuidado para fins académicos.

> 💡 **Compatibilidade**: Estrutura de dados optimizada para Google Vertex AI e Azure ML.

> 🔄 **Replicabilidade**: Todos os scripts são determinísticos com seeds fixas para reproduzibilidade.

---

**Última Atualização**: 14 de maio de 2026  
**Status**: ✅ Em Desenvolvimento Activo
