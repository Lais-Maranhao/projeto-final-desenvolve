# Guia de Preparação de Dados para Machine Learning

Este guia descreve o processo de preparação de dados implementado no notebook `notebooks/preparacao_ml.ipynb`. O objetivo é transformar os dados brutos em um formato adequado para treinar modelos de machine learning.

## 1. Pré-processamento Inicial
Antes das transformações principais, realizamos uma limpeza básica.

- **Tratamento de Valores Ausentes:**
  - Por quê? Modelos de machine learning não conseguem lidar com valores ausentes (NaN).
  - Como? Preenchemos os NaNs da coluna `Bed Grade` com a moda (valor mais frequente) e de `City_Code_Patient` com 0.

- **Conversão da Coluna 'Age':**
  - Por quê? A coluna `Age` é uma string (ex: '51-60') e precisa ser numérica.
  - Como? Convertemos cada intervalo de idade para sua média numérica (ex: '51-60' se torna 55.5).

## 2. Remoção de Duplicatas
- Por quê? Linhas duplicadas podem introduzir viés no modelo.
- Como? Usamos `drop_duplicates()` para garantir que cada registro seja único.

## 3. Tratamento de Outliers (Método IQR)
- Por quê? Outliers (valores extremos) podem distorcer o treinamento do modelo.
- Como? Calculamos o Intervalo Interquartil (IQR) para cada coluna numérica e removemos as linhas que contêm valores fora do intervalo de 1.5 * IQR.

## 4. Transformação de Variáveis Assimétricas (Log)
- Por quê? Variáveis com distribuição muito assimétrica podem prejudicar o desempenho de alguns modelos.
- Como? Aplicamos a transformação de log (`np.log1p`) em colunas com alta assimetria, como `Admission_Deposit`.

## 5. Remoção de Variáveis Altamente Correlacionadas
- Por quê? Variáveis que são muito similares (alta correlação) são redundantes e podem causar problemas de multicolinearidade.
- Como? Calculamos a matriz de correlação e removemos uma das colunas de cada par com correlação acima de 0.95.

## 6. Agrupamento de Categorias Raras
- Por quê? Categorias com poucas amostras podem levar a um sobreajuste (overfitting).
- Como? Agrupamos categorias que aparecem em menos de 1% dos dados em uma única categoria "OUTRA".

## 7. Encoding de Variáveis Categóricas (One-Hot Encoding)
- Por quê? Modelos matemáticos precisam de inputs numéricos.
- Como? Convertemos colunas categóricas em múltiplas colunas binárias (0 ou 1) usando `pd.get_dummies()`.

## 8. Normalização das Variáveis Numéricas
- Por quê? É importante que as variáveis numéricas estejam na mesma escala para que o modelo não atribua pesos indevidos a variáveis com magnitudes maiores.
- Como? Usamos o `StandardScaler` para padronizar as colunas numéricas, resultando em uma média de 0 e desvio padrão de 1.
