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
- Verificação do Tipo de Dados;
- Verificação de Valores Nulos;
- Verificação da Distribuição da Variável Target (Class);
Base bastante desbalanceada com apenas 0,17% dos dados correspondentes à classe 1.
- Matriz de Correlação
As principais variáveis correlacionadas à Class são, respectivamente: V17, V14, V12, V10, V16, V3, V7, V18 e V11.

