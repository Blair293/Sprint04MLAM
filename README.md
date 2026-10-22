# Classificação de Energia Renovável

## Sobre o projeto

Este projeto utiliza o dataset **Renewable Energy Production Dataset (2010–2020)** para analisar e classificar a variável `Energy_Class` com Python. O trabalho segue as etapas solicitadas na atividade: preparação dos dados, análise de correlação, aplicação de um modelo de classificação linear e avaliação do desempenho em dois cenários de treinamento e teste.

## Objetivos

- Carregar a base de dados em um DataFrame com pandas.
- Converter a variável-alvo `Energy_Class` para valores numéricos.
- Construir e analisar a matriz de correlação entre as features, incluindo a variável-alvo codificada.
- Treinar um modelo de classificação linear.
- Comparar o desempenho do modelo com 60% dos dados para treinamento e 40% para teste, e com 85% para treinamento e 15% para teste.
- Avaliar os resultados por meio de matrizes de confusão, acurácia, precisão e recall.

## Tecnologias utilizadas

- Python
- pandas e NumPy
- Matplotlib e Seaborn
- scikit-learn
- Jupyter Notebook

## Arquivos do repositório

- `Renewable_Energy_Data.csv` — base de dados utilizada no projeto.
- `Analise_Renewable_Energy_Notebook.ipynb` — notebook com o código, as análises, os gráficos, o treinamento e a avaliação do modelo.
- `resultados/` — pasta destinada aos arquivos exportados, como matriz de correlação, matrizes de confusão, métricas e relatórios.

## Metodologia

### 1. Preparação e análise dos dados

O notebook carrega o arquivo CSV e codifica `Energy_Class`. Quando as classes são `Low`, `Medium` e `High`, o mapeamento utilizado é:

| Classe | Código |
|---|---:|
| Low | 0 |
| Medium | 1 |
| High | 2 |

As variáveis categóricas são transformadas em variáveis indicadoras (*One-Hot Encoding*) para permitir o cálculo da matriz de correlação. A correlação de Pearson é utilizada para observar associações lineares entre as variáveis e a variável-alvo.

A decisão inicial é manter as features disponíveis, pois uma correlação linear baixa com o alvo, isoladamente, não significa que uma variável não possa contribuir para a classificação. A matriz é interpretada como uma ferramenta de diagnóstico, e o desempenho é avaliado nos conjuntos de teste.

### 2. Modelo de classificação

O modelo escolhido é a **Regressão Logística**, disponível no scikit-learn. Apesar do nome, ela é utilizada aqui para classificação. É considerada um modelo linear porque calcula combinações lineares das features transformadas para estimar as probabilidades das classes, estabelecendo fronteiras de decisão lineares no espaço transformado.

O pré-processamento é executado dentro de um pipeline. Assim, a padronização das variáveis numéricas e a codificação das variáveis categóricas são ajustadas a partir dos dados de treinamento, evitando usar informações do conjunto de teste durante o treinamento.

### 3. Cenários de avaliação

O mesmo modelo e a mesma semente aleatória são usados para comparar os dois cenários:

- **Cenário 1:** 60% dos dados para treinamento e 40% para teste.
- **Cenário 2:** 85% dos dados para treinamento e 15% para teste.

A divisão é estratificada para preservar, aproximadamente, a proporção das classes em cada conjunto.

### 4. Métricas

O notebook apresenta:

- **Matriz de confusão:** compara as classes reais com as classes previstas.
- **Acurácia:** proporção total de previsões corretas.
- **Precisão ponderada:** resume a precisão das classes, ponderada pelo número de exemplos de cada classe.
- **Recall ponderado:** resume a proporção de exemplos corretamente identificados em cada classe, também ponderada pelo número de exemplos.

Os resultados devem ser interpretados em conjunto. O cenário com 40% de teste oferece uma avaliação baseada em mais observações, mas deixa menos dados para o treinamento. Já o cenário com 15% de teste permite treinar com mais dados, mas a avaliação pode ser mais sensível à composição de um conjunto de teste menor.

## Como executar o notebook

1. Baixe ou clone este repositório.
2. Mantenha `Renewable_Energy_Data.csv` na mesma pasta do notebook.
3. Instale as dependências, se necessário:

   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn jupyter
   ```

4. Abra `Analise_Renewable_Energy_Notebook.ipynb` no Jupyter Notebook, JupyterLab ou Google Colab.
5. Execute as células em ordem.

O notebook apresenta as análises, os gráficos, as matrizes de confusão e as métricas dos dois cenários.

## Observação sobre os resultados

Os valores das métricas devem ser consultados após a execução do notebook com o dataset incluído no repositório. A correlação de Pearson, por si só, não determina a capacidade preditiva de uma feature; por isso, a decisão sobre o modelo também considera as métricas e as matrizes de confusão.

## Fonte do dataset

Kaggle — [Renewable Energy Production Dataset (2010–2020)](https://www.kaggle.com/datasets/itsrohithere/renewable-energy-production-dataset-2010-2020/data)
