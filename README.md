# Projeto de Estágio - Análise e Limpeza de Dados

Este repositório contém o trabalho de estágio focado em análise, processamento e limpeza de dados utilizando Python e Jupyter Notebooks.

## 📋 Descrição

Este projeto é desenvolvido como parte do curso de Licenciatura em Inteligência Artificil e Ciências de Dados. O objetivo principal é trabalhar com diferentes conjuntos de dados públicos, aplicar técnicas de limpeza de dados, análise exploratória e preparação de dados para modelos de machine learning.

## 📁 Estrutura do Projeto

```
projeto-estagio/
├── Untitled.ipynb                    # Notebook principal de processamento de dados
├── adults.csv                        # Dataset bruto: dados de adultos
├── adults_data.csv                   # Dataset de adultos (versão processada)
├── data_clean_final.csv              # Dataset final limpo
├── iris.data                         # Dataset Iris (dados brutos)
├── azure/                            # Integração com Azure
├── open source iris/                 # Análise do dataset Iris
├── open source breast cancer/        # Análise do dataset Breast Cancer
├── Modelo 2025_26 Relatório de Estágio - Lic. em Engª Informática 2.docx
└── README.md
```

## 🛠️ Tecnologias Utilizadas

- **Python 3.13.9**
- **Jupyter Notebook** - Para análise interativa e documentação
- **Pandas** - Processamento e manipulação de dados
- **NumPy** - Computação numérica
- **Azure** - Plataforma cloud (integração em desenvolvimento)

## 📊 Datasets

O projeto trabalha com os seguintes conjuntos de dados:

### 1. **Adults Dataset**
- Arquivo: `adults.csv`
- Contém dados demográficos e econômicos sobre adultos
- Usado para prever se a renda está acima ou abaixo de 50K

### 2. **Iris Dataset**
- Arquivo: `iris.data`
- Conjunto de dados clássico com características de flores iris
- Utilizado para classificação e análise exploratória

### 3. **Breast Cancer Dataset**
- Pasta dedicada: `open source breast cancer/`
- Dataset público para análise e classificação

## 🔧 Processamento de Dados

O notebook principal (`Untitled.ipynb`) realiza as seguintes operações:

1. **Carregamento de Dados**: Importa arquivos CSV com tipagem segura
2. **Limpeza de Estrutura**: 
   - Remove espaços em branco dos nomes de colunas
   - Substitui hífens por underscores (compatibilidade com Vertex AI)
3. **Tratamento de Valores Faltantes**:
   - Substitui `?` por `Unknown`
   - Remove linhas com valores ausentes
4. **Validação**:
   - Verifica forma do dataset
   - Confirma ausência de valores nulos
   - Identifica variáveis alvo

## 📈 Saída Esperada

Após o processamento do dataset adults:
- **Shape**: (30162, 15) - 30.162 linhas e 15 colunas
- **Valores Nulos**: 0 - Dataset completamente limpo
- **Variável Alvo**: `income` com valores ['<=50K', '>50K']

## 🚀 Como Usar

### Pré-requisitos

```bash
pip install pandas numpy jupyter
```

### Executar o Notebook

1. Clone o repositório:
```bash
git clone https://github.com/anapatriciagil74-arch/projeto-estagio.git
cd projeto-estagio
```

2. Inicie o Jupyter Notebook:
```bash
jupyter notebook
```

3. Abra o arquivo `Untitled.ipynb` e execute as células

### Gerar Dataset Limpo

Execute o notebook para gerar automaticamente o arquivo `adults_data_clean.csv`

## 📝 Relatório de Estágio

O documento oficial do relatório está disponível em:
- `Modelo 2025_26 Relatório de Estágio - Lic. em Engª Informática 2.docx`

## 🔗 Integração Azure

O projeto inclui integração com Microsoft Azure para:
- Armazenamento de dados em cloud
- Execução de modelos de machine learning
- Automação de pipelines de dados

*Veja a pasta `azure/` para mais detalhes*

## 📚 Datasets Públicos Utilizados

- **Adults Dataset**: Censo dos EUA
- **Iris Dataset**: Clássico dataset de iris (Ronald Fisher)
- **Breast Cancer Dataset**: Dados públicos de diagnóstico

## 👤 Autor

**Ana Patrícia Gil**
- GitHub: [@anapatriciagil74-arch](https://github.com/anapatriciagil74-arch)

## 📄 Licença

Este projeto é desenvolvido como trabalho acadêmico de estágio.

## ℹ️ Notas

- O dataset foi processado para remover valores ausentes e garantir compatibilidade com plataformas de ML como Google Vertex AI
- Nomes de colunas foram padronizados (sem hífens)
- Todos os valores faltantes foram tratados como `Unknown`

## 📧 Contato

Para dúvidas sobre este projeto, entre em contato através do GitHub.

---

**Última atualização**: 14 de maio de 2026
