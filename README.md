# treino-de-regressao-linear-sk-learning


**Explorando Novas Habilidades em Python!**

Olá, pessoal!

Estou animado para compartilhar algumas das novas habilidades que venho desenvolvendo em Python para análise de dados e machine learning. Recentemente, mergulhei em machine learning e regressões lineares usando um dataset de custos de seguros, com o objetivo de identificar as features mais importantes para prever os custos do seguro.

**Análise do Dataset:**
- Após carregar o dataset no Colab, realizei uma exploração inicial e verifiquei dados nulos e o formato dos dados.
- A idade mínima é 18 anos e a máxima é 64 anos, com a média e a mediana em 39 anos. 75% dos registros têm até 51 anos.
- 45% dos assinantes não têm filhos. Em relação ao IMC, não há grandes diferenças entre homens e mulheres em termos de tabagismo, com uma leve vantagem masculina.

**Insights Relevantes:**
- O custo do seguro aumenta com 1 a 3 filhos e diminui depois disso.
- O custo é mais alto para mulheres e um pouco mais baixo para homens.
- Usei gráficos e o método `corr()` da biblioteca Seaborn para identificar as principais variáveis associadas ao custo do seguro. As variáveis mais relevantes são: fumantes, idade e IMC.

**Modelo LinearRegressor:**
- MSE train: 0.0096
- MSE test: 0.0086

Ambos os MSEs baixos indicam um modelo estável e consistente. O R-quadrado de 0.750 sugere que cerca de 75% da variação nos custos é explicada pelas variáveis do modelo.

No vídeo, fiz um ajuste ao remover o intercepto, o que melhorou meu R² para 87%. Às vezes, um pequeno detalhe pode fazer uma grande diferença nas variações do seu modelo.

Dê uma olhada no vídeo para conferir os códigos e acompanhar minha evolução na área de dados.

