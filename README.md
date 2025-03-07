## Importação do LabelEncoder
Primeiro, importamos LabelEncoder da biblioteca sklearn.preprocessing. O LabelEncoder é usado para converter valores categóricos em valores numéricos.

## Codificação da coluna "profissao"
Criamos um objeto LabelEncoder chamado codificador_profissao.
Em seguida, aplicamos fit_transform() na coluna "profissao" da tabela, convertendo as profissões em números (por exemplo, cientista = 1, bombeiro = 2, etc.).

## Codificação da coluna "mix_credito"
Criamos um novo LabelEncoder, codificador_credito, e aplicamos fit_transform() na coluna "mix_credito", convertendo seus valores categóricos em números.

## Codificação da coluna "comportamento_pagamento"
Criamos outro LabelEncoder, codificador_pagamento, e aplicamos fit_transform() na coluna "comportamento_pagamento", transformando os valores categóricos dessa coluna em valores numéricos.

## Exibição das informações da tabela
Por fim, usamos display(tabela.info()) para verificar a estrutura da tabela, conferindo os tipos de dados e se as colunas foram corretamente convertidas.

## Definição da variável alvo (y)
Pegamos a coluna "score_credito" da tabela e armazenamos em y. Essa será a variável que queremos prever no modelo.

## Definição das variáveis preditoras (x)
Criamos x removendo as colunas "score_credito" (que é nosso alvo) e "id_cliente" (pois geralmente um ID não ajuda na previsão). O restante das colunas será usado como entrada para o modelo.

## Separação dos dados em treino e teste
Importamos train_test_split da biblioteca sklearn.model_selection.
Depois, usamos train_test_split() para dividir os dados em duas partes:
<div>
  x_treino e y_treino: usados para treinar o modelo.
</div>
<div>
  x_teste e y_teste: usados para testar o modelo.
</div>
Definimos test_size=0.3, o que significa que 30% dos dados serão usados para teste e 70% para treino.

## Importação dos Modelos
Importamos dois algoritmos de machine learning do sklearn:
<div>
  RandomForestClassifier (um modelo baseado em árvores de decisão).
</div>
KNeighborsClassifier (um modelo baseado em vizinhos mais próximos – KNN).

## Criação dos Modelos
Criamos dois modelos de IA:
<div>
  modelo_arvoredecisao → um classificador baseado em Random Forest.
</div>
modelo_knn → um classificador baseado no algoritmo KNN.

## Treinamento dos Modelos
<div>
  modelo_arvoredecisao.fit(x_treino, y_treino): Treinamos o modelo de árvore de decisão usando os dados de treino.
</div>
modelo_knn.fit(x_treino, y_treino): Treinamos o modelo KNN usando os mesmos dados de treino.

## Previsão de testes
Depois de treinar os modelos, usamos predict() para fazer previsões nos dados de teste:
<div>
  previsao_arvoredecisao = modelo_arvoredecisao.predict(x_teste): O modelo de árvore de decisão faz previsões com base nos dados de teste.
</div>
previsao_knn = modelo_knn.predict(x_teste): O modelo KNN faz o mesmo.

## Calculando a Acurácia
Importamos accuracy_score da biblioteca sklearn.metrics, que mede a precisão do modelo comparando os valores reais (y_teste) com as previsões feitas pelos modelos.
<div>
       accuracy_score(y_teste, previsao_arvoredecisao): Calculamos a acurácia do modelo de árvore de decisão.
</div>
<div>
  accuracy_score(y_teste, previsao_knn): Calculamos a acurácia do modelo KNN.
</div>
<div>
  Usamos display() para mostrar os resultados na tela.
</div>
Usamos pd.read_csv("novos_clientes.csv") para carregar uma nova tabela com informações de clientes que ainda não têm um score de crédito definido.

## Codificação das colunas categóricas
Como os modelos foram treinados com valores numéricos, precisamos transformar os dados categóricos da nova tabela da mesma forma que fizemos antes:
<div>
  profissao: Aplicamos codificador_profissao.transform() para converter profissões em números.
</div>
<div>
  mix_credito: Aplicamos codificador_credito.transform() para converter esse atributo em números.
</div>
comportamento_pagamento: Aplicamos codificador_pagamento.transform() para transformar essa coluna.

## Exibição da tabela transformada
Usamos display(tabela_novos_clientes) para visualizar a nova tabela e conferir se os dados foram corretamente transformados.

## Fazendo previsões com o modelo treinado
nova_previsao = modelo_arvoredecisao.predict(tabela_novos_clientes): Utilizamos o modelo de árvore de decisão para prever o score de crédito dos novos clientes.
<div>
  display(nova_previsao): Exibimos as previsões para ver quais scores foram atribuídos.
</div>
