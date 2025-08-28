# Projeto---Fraude-em-Cartoes
Projeto do Curso de Ciência de Dados da EBAC

## Introdução
**Cliente:** Banco Global Trust  
**Objetivo:** Detectar fraudes em transações de cartão de crédito, minimizando prejuízos e garantindo a segurança dos clientes.

**Base de Dados:**  
- Total de transações: 284.807  
- Fraudes identificadas: 492  
- Tipo de variáveis: numéricas, transformadas via PCA  
- Target: binária (1 = fraude, 0 = não fraude)

**Demanda do Cliente:**  
Desenvolver um modelo preditivo capaz de identificar fraudes de forma eficaz, **maximizando a acurácia** e **minimizando falsos negativos**.

## Análise dos Dados
- **Verificação do Tipo de Dados**
- **Verificação de Valores Nulos**
- **Verificação da Distribuição da Variável Target (Class)**
    - Base bastante desbalanceada com apenas 0,17% dos dados correspondentes à classe 1.
- **Matriz de Correlação**
    - As principais variáveis correlacionadas à Class são, respectivamente: V17, V14, V12, V10, V16, V3, V7, V18 e V11.

## Preparação dos Dados
- Separação da Base em X(features) e Y(variável target)
- Separação da Base em Treino e Teste
- Balanceamento com SMOTE

## Estratégia de Modelagem

A ideia é testar vários modelos **com e sem balanceamento**. O modelo com a **melhor performance** será escolhido para uma pesquisa mais ampla de **hiperparâmetros**.

### Modelos a serem testados:
- **Lineares:** Regressão Logística  
- **Baseados em árvores:** Random Forest e XGBoost  
- **Baseados em margens e hiperplanos:** SVM

## Comparação de Modelos

- **Regressão Logística:** recall 0.92, mas precisão muito baixa (0.16), gerando muitos falsos positivos.  
- **Random Forest vs XGBoost:** recall semelhante (RF: 0.85 | XGB: 0.86), precisão do XGBoost ligeiramente menor (0.80 vs 0.87).  
- **Tempo de execução:** RF ~600s | XGB ~5s.  

**Conclusão:**  
O XGBoost foi escolhido por combinar **alto recall para fraudes** e **eficiência computacional**. Próxima etapa: otimização de hiperparâmetros.

## Ajuste nos Hiperparâmetros

- **Método:** GridSearch  
- **Melhores parâmetros encontrados:**  
  - `colsample_bytree`: 0.8  
  - `gamma`: 0  
  - `learning_rate`: 0.1  
  - `max_depth`: 5  
  - `min_child_weight`: 1  
  - `n_estimators`: 200  
  - `reg_alpha`: 0.1  
  - `reg_lambda`: 1.5  
  - `subsample`: 1.0

 ## Resultados XGBoost com Hiperparâmetros

- **Classe 0:** Precision 1.00 | Recall 1.00  
- **Classe 1:** Precision 0.67 | Recall 0.87 | F1 0.76  
- **Matriz de Confusão:** [[56822, 42], [13, 85]]  

**Conclusão:**  
O XGBoost com os melhores hiperparâmetros apresenta **alto recall para fraudes** e **boa precisão**, sendo eficiente e confiável para identificar fraudes em transações de cartão de crédito.
