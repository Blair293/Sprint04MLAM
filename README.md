# Classificação de classes de energia renovável


## Integrantes
Arthur Araujo Massarioli - RM: 573308
Daniel Alejandro Pupo Martínez - RM: 573075
Victor Hugo Lavaqui - RM: 573838
Wendel Pedro Rezende - RM: 573126

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
