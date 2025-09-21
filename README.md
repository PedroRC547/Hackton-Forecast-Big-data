# Hackton-Forecast-Big-data

Este projeto tem como objetivo prever a quantidade semanal de vendas por ponto de venda (PDV) e por produto (SKU) para as cinco semanas de janeiro de 2023. A previsão é baseada no histórico de vendas de todo o ano de 2022 e foi desenvolvida para apoiar decisões de abastecimento, reposição e planejamento operacional no varejo.

A solução foi construída com foco em escalabilidade, clareza e inteligência de negócio combinando técnicas de machine learning com conhecimento prático de varejo.

1. Integração dos dados
Começamos reunindo três fontes essenciais: catálogo de produtos, histórico de transações e catálogo de PDVs. Com isso, conseguimos cruzar o que foi vendido, onde e por quem, formando a base para entender o comportamento de consumo.

2. Estruturação temporal
Transformamos datas em semanas e anos para alinhar os dados com o ritmo operacional do varejo. A previsão é semanal, então o modelo precisa enxergar os dados nesse mesmo compasso.

3. Foco no ano de 2022
Usamos apenas os dados de 2022 para garantir relevância e consistência. Isso evita que padrões antigos ou desatualizados interfiram na previsão de janeiro.

4. Agregação por semana, PDV e SKU
Agrupamos as vendas por semana, loja e produto, exatamente como o varejo pensa em reposição. Essa estrutura permite que o modelo aprenda padrões reais de consumo.

5. Criação da média móvel
Calculamos uma média móvel de 4 semanas para suavizar oscilações pontuais e destacar tendências. Essa feature ajuda o modelo a entender o ritmo de vendas sem depender de datas específicas.

6. Enriquecimento com atributos
Incorporamos variáveis como categoria, subcategoria, marca e tipo de loja. Esses atributos são cruciais para capturar o contexto de cada venda, afinal, uma água mineral não se comporta como um shampoo, e uma loja de bairro não vende como um hipermercado.

7. Codificação categórica
Transformamos os atributos em números usando LabelEncoder, mantendo consistência entre treino e previsão futura. Isso permite que o modelo processe as informações corretamente.

8. Tratamento da variável target
Aplicamos log na quantidade vendida para lidar com a distribuição assimétrica dos dados. Produtos com vendas muito altas ou muito baixas podem distorcer o aprendizado, o log ajuda a equilibrar isso.

9. Separação entre treino e teste
Dividimos os dados respeitando a ordem temporal, simulando uma previsão real. O modelo aprende com o passado e é testado com dados que ele nunca viu.

10. Treinamento com LightGBM
Escolhemos o LightGBM por sua eficiência e capacidade de lidar com grandes volumes de dados tabulares. Ele entrega bons resultados com baixo custo computacional.

11. Avaliação do modelo
Calculamos métricas como MAE, RMSE, MAPE e acurácia dentro de ±10%. Também analisamos o desempenho por faixa de volume, porque no varejo, produtos de alto giro exigem mais precisão do que os esporádicos.

12. Diagnóstico por faixa
Segmentamos os resultados em faixas como “baixo”, “médio” e “alto” volume. Isso revela onde o modelo está acertando bem e onde há espaço para ajustes.

13. Previsão para janeiro/2023
Geramos uma grade com todos os pares PDV/SKU que venderam em 2022 e aplicamos o modelo para prever as cinco semanas de janeiro. O resultado é um CSV pronto para abastecimento, planejamento ou integração com BI.
