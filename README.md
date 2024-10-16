# classificacao-titanic

Carregamento e pré-processamento dos dados.
Função carregar_dados: Insere três arquivos CSV: gender_submission.csv (gênero e previsão de sobrevivência), test.csv (dados de teste sem identificação), e train.csv (dados de treino com identificação de sobrevivência).

Função limpar_dados: Elimina as linhas com valores ausentes (incompletos) tanto nos dados de treinamento quanto nos de teste, utilizando o método dropna(). Em seguida, as informações limpas são armazenadas novamente em arquivos CSV.

Função selecionar_variaveis: Escolhe as colunas mais relevantes para a análise (classe, sexo, idade, tarifa e sobrevivência), convertendo a coluna "Sex" em variáveis dummy para simplificar a inserção no modelo (converter "male" para 0 e "female" para 1).

Aplicação do método k-NN
Função knn_modelo: Aplica o algoritmo K-Nearest Neighbors (k-NN) para categorizar as informações. Neste cenário, n_neighbors=3 indica que o modelo considerará os 3 vizinhos mais próximos para determinar a sobrevivência de um indivíduo, com base nas características fornecidas (classe, sexo, idade, tarifa).

O modelo é calibrado através da função knn.fit(X_train, y_train), na qual X_train representa as variáveis explicativas e y_train representa os rótulos de sobrevivência.

Avaliação de desempenho (acurácia e matriz de confusão)
Função avaliar_modelo: Avalia o modelo treinado, gerando as seguintes métricas:

Acurácia: Medida básica de desempenho, indicando a proporção de previsões corretas. Calculada por accuracy_score(y_test, y_pred).

Relatório de Classificação: Gera métricas detalhadas como precisão, recall e F1-score para cada classe (sobreviveu/não sobreviveu).

Matriz de Confusão: Representa visualmente o desempenho do modelo ao mostrar o número de previsões corretas e incorretas para cada classe. As diagonais principais mostram as previsões corretas e os outros elementos mostram os erros.

Heatmap: Um gráfico gerado com o seaborn para visualizar a matriz de confusão de forma mais clara.

Observações sobre os resultados e o que pode ser melhorado
Resultados iniciais: A acurácia e a matriz de confusão mostram como o modelo está se saindo na previsão de sobrevivência com base nas características fornecidas. No entanto, o k-NN pode ter desempenho limitado, especialmente em grandes conjuntos de dados ou quando as variáveis têm escalas diferentes (aqui, "Fare" e "Age" podem influenciar mais do que "Pclass", por exemplo).

Melhorias possíveis:

Normalização dos dados: Aplicar normalização ou padronização nas variáveis numéricas (Age, Fare) pode melhorar o desempenho do k-NN, que é sensível à escala dos dados.
Ajuste de hiperparâmetros: Testar diferentes valores para n_neighbors ou usar técnicas como validação cruzada para encontrar a melhor configuração.
Aumento de dados: Incluir mais variáveis ou preencher dados ausentes de maneira inteligente, em vez de simplesmente remover linhas, pode melhorar o desempenho do modelo.
