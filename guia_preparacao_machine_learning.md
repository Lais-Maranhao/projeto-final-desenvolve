# Guia de preparação de dados para Machine Learning

## 1. Remoção de duplicatas
- Por quê? Linhas duplicadas podem distorcer o aprendizado do modelo.
- Como? Usamos `drop_duplicates()` para garantir que cada linha seja única.

## 2. Tratamento de outliers (IQR)
- Por quê? Outliers podem atrapalhar o modelo.
- Como? Calculamos o intervalo interquartil (IQR) e removemos valores extremos.

## 3. Transformação de variáveis assimétricas (log)
- Por quê? Variáveis muito assimétricas dificultam o aprendizado.
- Como? Aplicamos `np.log1p()` nas colunas com assimetria alta.

## 4. Remoção de variáveis altamente correlacionadas
- Por quê? Variáveis muito parecidas podem confundir o modelo.
- Como? Calculamos a matriz de correlação e removemos colunas redundantes.

## 5. Agrupamento de categorias raras
- Por quê? Categorias pouco frequentes podem gerar problemas de generalização.
- Como? Substituímos categorias com menos de 1% das linhas por “OUTRA”.

## 6. Encoding das variáveis categóricas (OneHot)
- Por quê? Modelos só entendem números. O OneHot transforma cada categoria em uma coluna binária.
- Como? Usamos `pd.get_dummies()` para criar essas colunas.

## 7. Normalização das variáveis numéricas
- Por quê? Modelos funcionam melhor quando os dados estão na mesma escala.
- Como? Usamos o `StandardScaler` para padronizar as colunas numéricas.

---

Se quiser exemplos práticos ou testar cada etapa separadamente, posso te ajudar!

---

Sobre o dataset limpo para análise: foi salvo como `data/train_data_limpo.csv`. Se não encontrar, execute novamente a célula que gera esse arquivo no notebook. Se precisar, posso te mostrar o código para garantir que ele seja criado.