# PROJETOAPLICADO3_2025.2


## Recomendações Inteligentes para Alimentação Saudável: Personalização a partir de preferências do usuário


COMPONENTE CURRICULAR:
PROJETO APLICADO III

GRUPO 12:
* Marcela Quaresma Soares - 10433423
* Mariana Mayume Caniza - 10290174
* Stella Amaral de Campos - 10441310

## 📋 Índice
---
## 📋 Índice
---

* [1. Resumo do Projeto](#1-resumo-do-projeto-visão-geral)
* [2. Metodologia (Pipeline)](#2-metodologia-pipeline)
* [3. Implementação e Avaliação](#3-implementação-e-avaliação)
    * [Desempenho das Métricas (Resultados)](#desempenho-das-métricas-resultados)
* [4. Coerência Semântica (Análise Qualitativa)](#4-coerência-semântica-análise-qualitativa)


### 🌟 1. Resumo do Projeto (Visão Geral)
O projeto visa implementar e avaliar um sistema de recomendação de restaurantes usando o algoritmo K-Nearest Neighbors (KNN) Item-Based.
A solução dialoga com o ODS 11 da ONU (Cidades e Comunidades Sustentáveis), auxiliando na organização e acesso a serviços urbanos.
| Ponto-Chave | Detalhe |
| :--- | :--- |
| **Problema** | Sobrecarga de opções em grandes centros urbanos. |
| **Solução** | Sistema de Recomendação de Restaurantes. |
| **Dados** | **Entree Chicago Recommendation Data** (UCI Machine Learning Repository). |
| **Modelo** | **KNN Item-Based** com similaridade do Cosseno. |
| **Representação**| **TF-IDF** (Term Frequency-Inverse Document Frequency). |

### 🛠️ 2. Metodologia (Pipeline)
A metodologia seguiu o ciclo padrão de um projeto de Machine Learning.

Processo: Definição do Problema → Coleta de Dados → Pré-processamento → Implementação do Algoritmo → Treinamento → Avaliação → Otimização.

Pré-processamento: A base de dados (que inclui informações de 8 cidades como Chicago e Nova York ) foi unificada , e os atributos dos restaurantes (como tipo de cozinha e ambiente ) foram vetorizados com a técnica TF-IDF.

### ⚙️ 3. Implementação e Avaliação
O modelo KNN Item-Based foi treinado para calcular a similaridade entre os restaurantes com base em seus atributos vetorizados por TF-IDF20.
Configuração: 
* $k=50$ vizinhos,
* Métrica do Cosseno,
* implementado com scikit-learn.

Avaliação Offline: Utilizou-se o histórico de sessões de interação. 
O último restaurante exibido foi a semente, e o escolhido foi o item relevante.
Métricas Chave: 
* Precision@k,
* NDCG@k,
* MRR (Mean Reciprocal Rank).

**Desempenho das Métricas (Resultados):**
A Tabela 1 apresenta os valores médios das métricas de desempenho para diferentes valores de k.

| k | Precision/Recall (Hit Rate) | NDCG | MRR |
| :---: | :---: | :---: | :---: |
| 3 | 0.011 | 0.009 | 0.008 |
| 5 | 0.019 | 0.012 | 0.009 |
| 10 | 0.035 | 0.017 | 0.011 |
| 15 | 0.042 | 0.019 | 0.012 |
| 20 | 0.052 | 0.021 | 0.013 |
| 30 | 0.063 | 0.023 | 0.013 |
| 40 | 0.089 | 0.028 | 0.014 |
| 50 | 0.103 | 0.031 | 0.014 |

*Legenda: k: número de vizinhos; NDCG: Normalized Discounted Cumulative Gain; MRR: Mean Reciprocal Rank.*
Observação: A Precision (Hit Rate) cresceu de 1,1% $(k=3)$ para 10,3% $(k=50)$, indicando que o aumento de $k$ melhora a cobertura, mas o baixo valor de MRR sugere limitações no ranqueamento, revelando que o item relevante nem sempre aparece no topo da lista

### 💡 4. Coerência Semântica (Análise Qualitativa)
A avaliação qualitativa complementa os resultados, demonstrando a **coerência semântica** das recomendações e validando a abordagem KNN Item-Based. 
O modelo consegue agrupar itens por atributos comuns, reproduzindo relações de similaridade plausíveis.

| Item Semente | Recomendações (5 mais similares) | Coerência Semântica |
| :--- | :--- | :--- |
| **Cafe Diem** | Peggy Sue's Diner, Einstein's, Brother Juniper's, OK Cafe, Blue Diner | Semelhantes em estilo: **"Diner" ou "Café"**. |
| **Alfredo's Italian Restaurant** | Nino's, Toni's Casa Napoli, Asti Trattoria, Altobeli's Fine Italian Cuisine, Ray's New York Pizza  | Fortemente focadas em **Culinária Italiana**. |
| **Sushi Zen** | Tatany, Meriken, Kamehachi, Iso, Restaurant Two Two Two  |Fortemente focadas em **Culinária Japonesa/Sushi**. |

**Nota:** Os exemplos ilustram que o modelo KNN identifica corretamente a similaridade dos atributos (culinária, faixa de preço, ambiente), mesmo sem dados explícitos de avaliação do usuário.
