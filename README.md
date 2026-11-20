# DEsafio Final - 

## Objetivo
Desenvolver um pipeline de Ciência de Dados para prever falhas mecânicas em equipamentos industriais.

## Dataset
A base possui 10.000 registros e 14 colunas.

A variável alvo é `falha_maquina`:
- `0`: funcionamento normal
- `1`: falha mecânica

## Variáveis não utilizadas como preditoras
- `udi`: identificador do registro.
- `id_produto`: identificador do produto.
- `falha_twf`, `falha_hdf`, `falha_pwf`, `falha_osf`, `falha_rnf`: motivos específicos de falha, utilizados somente para histórico/consulta segundo as anotações de Engenharia.

## Pipeline
1. Análise exploratória (EDA)
2. Limpeza e tratamento
3. Feature Engineering
4. Divisão 80/20 com `stratify=y`
5. SMOTE somente no treino
6. StandardScaler somente para KNN
7. Teste de hiperparâmetros
8. Comparação final por acurácia no teste

## Feature Engineering
Foi criada a variável:

`potencia = velocidade_rotacao_rpm * torque_nm`

## Modelos
- KNN: K = 3, 5, 7, 9, 11
- Árvore de Decisão: `max_depth` = 3, 5, 7, None

## Execução

```bash
pip install -r requirements.txt
jupyter notebook Projeto_Final.ipynb
```

O notebook utiliza caminho relativo:

`manutencao_preditiva.csv`

## Resultados observados na execução de referência

| Modelo | Configuração | Acurácia teste |
|---|---:|---:|
| KNN | K=3 | 0.9265 |
| Árvore de Decisão | max_depth=3 | 0.8645 |
| Árvore de Decisão | max_depth=5 | 0.8665 |
| Árvore de Decisão | max_depth=7 | 0.9390 |
| Árvore de Decisão | max_depth=None | 0.9485 |

A maior acurácia de teste observada foi da Árvore de Decisão com `max_depth=None`, com 94,85%.

> Os valores acima são resultados da execução realizada sobre a base fornecida. O notebook recalcula os resultados ao ser executado.

## GitHub
Recomenda-se utilizar:
- `main`: versão final
- `develop`: integração
- feature branches: uma por funcionalidade
