# Classificação de classes de energia renovável

Projeto desenvolvido em Python para analisar o dataset `Renewable_Energy_Data.csv` e classificar a variável-alvo `Energy_Class`, conforme os requisitos do PDF.

## O que o projeto faz
1. Carrega o CSV em um DataFrame pandas.
2. Codifica `Energy_Class` como `Low = 0`, `Medium = 1`, `High = 2`.
3. Codifica variáveis categóricas com one-hot encoding para a matriz de correlação.
4. Salva a matriz de correlação e as correlações com a variável-alvo.
5. Treina uma **Regressão Logística**, classificador linear do scikit-learn.
6. Compara dois cenários com `random_state=42` e divisão estratificada:
   - 60% treino / 40% teste;
   - 85% treino / 15% teste.
7. Gera matrizes de confusão, acurácia, precisão ponderada, recall ponderado e relatórios de classificação.

## Por que Regressão Logística?
Apesar do nome, a regressão logística é usada para classificação. Ela calcula combinações lineares das variáveis de entrada e transforma os resultados em probabilidades por classe. As fronteiras de decisão são lineares no espaço das features após o pré-processamento.

## Decisão sobre as features
A matriz de correlação é usada como diagnóstico de relações lineares, não como único critério de seleção. Como correlações fracas com o alvo não provam que uma variável não tenha valor preditivo, o projeto mantém todas as features e compara o desempenho do modelo. As variáveis categóricas são transformadas por one-hot encoding dentro do pipeline, e a padronização é ajustada apenas nos dados de treino para reduzir vazamento de informação.

## Como executar
Requer Python 3.10+ e os pacotes:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

Execute, na pasta do projeto:
```bash
python analise_energia.py
```

Os arquivos gerados serão salvos na pasta `resultados/`.

## Estrutura
- `Renewable_Energy_Data.csv`: base usada.
- `analise_energia.py`: código completo da análise e dos dois cenários.
- `resultados/`: matrizes, gráficos, métricas e resumo interpretativo gerados após a execução.

## Observações
Os resultados numéricos dependem do arquivo CSV incluído. O vídeo de entrega deve mostrar a execução do script, explicar os gráficos e comparar os dois cenários. O arquivo `.txt` final de entrega solicitado pelo enunciado deve conter os nomes completos e RMs dos integrantes, o link do vídeo não listado e o link do repositório GitHub.
