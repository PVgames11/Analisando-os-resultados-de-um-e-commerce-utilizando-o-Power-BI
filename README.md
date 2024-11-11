# Analisando-os-resultados-de-um-e-commerce-utilizando-o-Power-BI
Hoje venho apresentar um projeto de Análise de Dados utilizando o Power BI, com o objetivo de efetuar análise financeira e uma análise de clientes.



Cenário
Um e-commerce almeja estudar as suas vendas e assim, traçar a melhor estratégia para alavancar seus resultados. Assim solicitou alguns indicadores como Quantidade de vendas, Valor total de vendas com frete e sem frete, Quantidade de clientes e Média de renda dos clientes.

Fonte de Dados
Nessa análise foi utilizada um dataset em formato .xlsx (Excel) e trata - se de dados fictícios apenas para estudo e para portifólio.

Preparação do Dados
Após a análise e exploração dos dados, verificou-se que não havia necessidade de ajustes adicionais, pois os dados já estavam adequados. A única alteração necessária foi a criação de uma coluna chamada "Faixa de Renda", que categorizou os valores da coluna "Renda" em intervalos específicos. Esses intervalos foram definidos da seguinte forma: até 1.750, até 2.500, até 5.000, até 7.500, até 10.000 e acima de 10.000. Para implementar essa classificação, foi utilizada a seguinte medida DAX:

Faixa Renda = 

SWITCH(

    TRUE(),

    'Base cliente'[renda] <= 1750, "Até 1.750",

    'Base cliente'[renda] <= 2500, "Até 2.500",

    'Base cliente'[renda] <= 5000, "Até 5.000",

    'Base cliente'[renda] <= 7500, "Até 7.500",

    'Base cliente'[renda] <= 10000, "Até 10.000",

    "Acima de 10.000"

)

Essa coluna facilita a segmentação e análise dos dados de renda, permitindo a criação de relatórios e visualizações baseados em faixas de valores bem definidas.



Análise Exploratória
Agora irei mostrar as medidas que foram criadas usando o DAX para melhorar a análise dos gestores.

Criando a medida Venda com frete:
Vendacomfrete = SUM('base compra'[Preço_com_frete])
Criando a medida Venda sem frete:
Vendasemfrete = SUM('base compra'[Preço])
Criando a medida Venda total:
Venda total = [Vendacomfrete] + [Vendasemfrete]
Criando a medida Quantidade de Vendas:
Quantidade de Vendas = COUNT('base compra'[idcompra])
Criando a medida Quantidade de clientes:
Quantidade de clientes = COUNT('Base cliente'[cliente_Log])
Criando a medida média de rendas:
Média de renda = AVERAGE('Base cliente'[renda])

Visualização dos dados
Ficando assim os dois dashboard um de vendas e um de clientes

![image](https://github.com/user-attachments/assets/13df46ff-107c-4a01-a0f1-116a9500a014)
![image](https://github.com/user-attachments/assets/da3adf9d-f518-4ab9-ba13-547e8748dd71)



Insights para os gestores
Se os gestores fossem pedir alguns insights para mim como um analista de dados, eu falaria para ele investir mais em São Paulo e Rio de Janeiro que são que geram mais lucros, continuar investindo em anúncios na internet, mobile e aplicativo e investir em mais produtos que os clientes que tem a sua faixa de renda acima dos 10.000 reais.

Se quiser ver melhor esse dashboard clique nesse link:https://app.powerbi.com/view?r=eyJrIjoiMWU4YTUwOTAtZGEwYS00NmM2LTk2YzQtY2RlMjE3NDlhMWFhIiwidCI6ImIyYjM3MjZjLTM5ZjItNGVmMS04MTRlLWFmM2QwMDA4ZDE3MyJ9
