Objetivo: Avaliar qual feature pesa mais na determinação do valor do custo do seguro.




Este DataFrame contém valores fictícios de seguros de vida. Meu objetivo aqui é demonstrar como a regressão linear pode ser utilizada para prever esse tipo de caso. Irei usar algumas métricas de avaliação do modelo e determinar quais features mais influenciam o valor do seguro. Em seguida, farei alguns testes de previsão do valor de custo com o modelo de regressão linear e mostrarei a diferença entre o valor predito e o valor real.
DataFrame original





![Captura de tela 2024-09-10 140202](https://github.com/user-attachments/assets/c83466ab-22f6-4864-9ae8-70dc996aef16)





Começo pela parte de limpeza dos dados no DataFrame, verificando os dados nulos. Temos 3 dados faltantes na coluna "sexo", que serão excluídos do modelo em sequência. Antes de fazer a exclusão, utilizo df.describe() para verificar algumas características estatísticas do DataFrame, como contagem de todas as colunas, média, mediana, percentis, desvio padrão, valores mínimos e máximos.
Com df.isnull().sum(), faço a contagem oficial dos dados nulos e, em seguida, uso df.dropna(inplace=True) para excluir os dados nulos do DataFrame.
Após isso, utilizo o código:
python
for column in df.columns:
    print(df[column].value_counts())
    print('\n')
para fazer uma contagem de todos os dados distintos que tenho, coluna por coluna. Isso também me ajuda a visualizar o que irei plotar nos gráficos para comparar os dados.
Trouxe aqui alguns insights interessantes:
Comparação de fumantes e IMC por sexo:
O sexo masculino apresenta um maior número de fumantes, enquanto há um empate entre os sexos no número de não fumantes.
Imagem

![fumantes -  sexo](https://github.com/user-attachments/assets/b1c3ed08-2005-4bbb-b674-fc0c2c0e6f20)





Quantidade de filhos por custo de seguros:
No caso de 2 a 3 filhos, para o sexo feminino, temos um aumento nos valores do seguro. Já a partir do quarto filho, há uma queda no valor do seguro. Para o sexo masculino, o custo do seguro aumenta a partir do segundo filho e se mantém até o quarto, havendo uma queda nos valores após esse ponto.

![linha custo -  quantidade de filho](https://github.com/user-attachments/assets/f5121c1d-a078-4948-85b0-a23cc61acb4b)






Aqui verifiquei os valores do custo do seguro e se eles seguem uma padronização, que chamamos de normal ou gaussiana.


![gaussiana](https://github.com/user-attachments/assets/5b5f74b0-a756-41bc-99c9-dad9379dd340)






Agora plotei um gráfico que relaciona a idade do contratante e a quantidade de filhos que ele possui. Como esperado, temos uma queda na quantidade de filhos a partir do terceiro.


![gaussiana](https://github.com/user-attachments/assets/711f8b01-1008-4160-af15-758234efaef3)




apliquei a tecnica de model select para descobrirmos a primeira resposta e antes de treinar o modelo de regressão lienear 
![Captura de tela 2024-09-11 131228](https://github.com/user-attachments/assets/713513ce-46b5-4c65-86b5-5d979dcd2427)

estas são as 4 colunas que respondem a pergunta  qual feature pesa mais na determinação dos valores de custo de um seguro de vida , temos um R2 de o.096 e um R2 ajustado de 0.094  , o R2 e o R2 ajustado são metricas que explica o quanto estes dados explicam meu modelo de regressão linear . quanto mais proximo de 1 mais ele confirma a validação do meu modelo


Após todas essas análises, escalonei os dados para que ficassem na mesma escala e comecei a divisão entre treino e teste. Antes disso, apliquei o OrdinalEncoder nas variáveis categóricas, transformando-as em 0 e 1 ou escalando conforme um número ordinal.
Avaliação do Modelo de Regressão Linear:
Após treinar um modelo de regressão linear com as variáveis independentes (IMC, quantidade de filhos, idade, fumante) para prever os custos do seguro, avaliei o desempenho do modelo utilizando o Mean Squared Error (MSE) e o R² (Coeficiente de Determinação), tanto para o conjunto de treino quanto para o de teste.
Resultados:
• Erro Quadrático Médio (MSE):
o Treino: O MSE do conjunto de treino foi de 0,0096%, indicando que o modelo apresenta um erro baixo na previsão dos custos de seguro com os dados de treino.
o Teste: O MSE no conjunto de teste foi de 0,0086%, confirmando que o modelo mantém um erro baixo ao prever dados não vistos anteriormente.
O MSE mede a diferença média ao quadrado entre os valores reais e previstos e, nesse caso, o erro é bastante baixo, sugerindo um bom ajuste do modelo.
• Coeficiente de Determinação (R²):
o Treino: O R² no conjunto de treino foi de 74,22%, mostrando que o modelo explica 74,22% da variação nos custos de seguro com os dados de treino.
o Teste: No conjunto de teste, o R² foi de 76,94%, indicando uma leve melhora, com o modelo sendo capaz de explicar 76,94% da variação nos dados de teste.
O R² varia de 0 a 100% e indica o quanto o modelo consegue explicar a variação da variável alvo com base nas variáveis preditoras. Nesse caso, os valores de R² sugerem que o modelo é relativamente bom em explicar a variação dos dados, embora ainda haja espaço para melhorias.

Na parte final coloquei 4 gráfico para verificar o quanto o modelo acerto comparando os valores reais dos preditos .


![regressão linear](https://github.com/user-attachments/assets/83a0c043-509f-4e45-b52e-d09a358a45a5)




Este ultimo nos mostra o quanto o modelo acerto sendo a parte  laranja os preditos e a azul o valores reais

![valor real  - valor predito](https://github.com/user-attachments/assets/378091ba-1ad8-4f76-8c18-0831f466f03b)




Conclusão:
O modelo apresentou uma performance consistente tanto no conjunto de treino quanto no de teste, com erros muito baixos (MSE) e uma boa capacidade de explicação da variância (R²) nos custos de seguro. A ligeira melhora no conjunto de teste é um bom sinal de generalização, indicando que o modelo não está sofrendo de overfitting e pode ser usado para previsões em novos dados.
Além disso, foi ajustado um modelo de regressão utilizando o pacote statsmodels, que forneceu um resumo estatístico detalhado, ajudando a entender a significância das variáveis preditoras no resultado.

