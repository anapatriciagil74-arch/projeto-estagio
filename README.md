# Exploração e Teste de Técnicas de AutoML

**Autora:** Ana Patrícia Gil  
**Instituição:** Universidade de Évora - Licenciatura em Inteligência Artificial e Ciências de Dados  
**Empresa:** KPMG Portugal — Departamento de Tech Consulting, equipa de Data & Analytics  
**Orientador na Empresa:** Nuno Miranda (Senior Manager)  
**Orientador no Departamento:** Teresa Gonçalves  
**Data:** Março–Maio 2026

---

## Descrição

Este projeto consiste numa avaliação prática e comparativa de ferramentas e plataformas de AutoML (Automated Machine Learning), desenvolvida no âmbito do Estágio-Projeto 2025/2026. O objetivo é apoiar futuras decisões de seleção tecnológica em projetos empresariais da equipa de Data & Analytics da KPMG.

---

## Ferramentas Avaliadas

### Open-Source
| Ferramenta | Paradigma | 
|---|---|---|
| TPOT | Programação genética |
| AutoGluon | Ensemble multi-nível | 
| H2O AutoML | Stacking + interpretabilidade | 
| AdaNet | Redes neuronais adaptativas | 

### Plataformas Cloud
| Plataforma | Fornecedor |
|---|---|
| Azure ML AutoML | Microsoft |
| SageMaker Canvas | Amazon Web Services |
| Vertex AI AutoML | Google Cloud |

---

## Datasets Utilizados

| Dataset | Registos | Features | Tipo de Problema |
|---|---|---|---|
| Iris | 150 | 4 | Classificação multiclasse |
| Breast Cancer Wisconsin | 569 | 30 | Classificação binária |
| Adult Income | 30.162 | 14 | Classificação binária |

---

## Estrutura do Repositório
├── .ipynb_checkpoinst
├── AzureML AutoML/
│   ├── AzureOutputsAndLogs.zip
│   ├── test.txt
│   └── data.csv
├── Google Vertex AI/
│   ├── adults.csv
│   ├── adults_data_clean.csv
│   ├── model-75315556....
│   ├── pre-processamento_adults.ipynb
│   └── test.txt
├── Open Source Breast Cancer Wisconsin/
│   ├── BreastCancer.ipynb
│   └── data.csv
├── Open Source Iris/
│   ├── adanet_iris.ipynb
│   ├── autogluon_iris.ipynb
│   ├── h2o_iris.ipynb
│   ├── tpot_iris.ipynb
│   ├── config_adanet.json
│   ├── config_autogluon.json
│   ├── config_h2o.json
│   └── config_tpot.json
├── SageMaker Canvas/
│   ├── SageMakerAutopilotCandidateDefinitionNotebook.ipynb
│   ├── data.csv
│   └── test.txt
└── README.md
└── 58385.pdf
---

## Requisitos

### Python e Ambiente
- Python 3.8+
- Anaconda (recomendado para gestão de ambientes virtuais)
- Jupyter Notebook / JupyterLab
- Sistema operativo: Windows 11 (testado)

### Bibliotecas Principais
```bash
pip install pandas numpy matplotlib seaborn scikit-learn
pip install tpot
pip install autogluon
pip install h2o
pip install adanet
```

> **Nota:** Recomenda-se criar um ambiente virtual separado para cada ferramenta, devido a potenciais conflitos de dependências.

### Ferramentas não compatíveis com Windows
As seguintes ferramentas foram excluídas por incompatibilidade com o ambiente Windows:
- **Auto-sklearn** — exclusivo para Linux
- **AutoFolio** — exclusivo para Linux
- **AutoDL** — dependente de versões antigas de PyTorch/TensorFlow

---

## Resultados Principais

| Ferramenta | Modelo Final (Iris) | F1 (Iris) | Modelo Final (BCW) | F1 (BCW) |
|---|---|---|---|---|
| TPOT | GaussianNB | 0.97 | GaussianNB | 0.96 |
| AutoGluon | WeightedEnsemble_L2 | 1.00 | WeightedEnsemble_L2 | 0.98 |
| H2O AutoML | DeepLearning | 0.96 | GLM | 0.98 |
| AdaNet | LinearEstimator | 0.86 | TensorFlow DNN | 0.95 |

---

## Conclusões

- **Não existe uma ferramenta universalmente superior.** A escolha deve ser guiada pelo contexto, pelos dados e pelos requisitos operacionais.
- **TPOT** — ideal quando a exportabilidade do pipeline como código Python é prioritária.
- **AutoGluon** — melhor escolha quando o desempenho preditivo é o critério dominante.
- **H2O AutoML** — melhor equilíbrio entre desempenho e interpretabilidade; recomendado em projetos de consultoria onde a explicabilidade é um requisito.
- **AdaNet** — mais adequado a contextos de investigação académica.
- **SageMaker Canvas** — ideal para prototipagem rápida e provas de conceito.
- **Azure ML AutoML** — preferível em projetos regulados que exigem auditabilidade.
- **Vertex AI AutoML** — recomendado para organizações já integradas no ecossistema Google Cloud.

---


