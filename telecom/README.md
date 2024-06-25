# **INTRODUÇÃO**
Este conjunto de dados contém 2 tabelas em formato CSV, retiradas do Kaggle em: [site do trabalho](https://www.kaggle.com/code/tmadjid/telecom-churn-eda)
"A tabela de rotatividade de clientes contém informações sobre todos os 7.043 clientes de uma empresa de telecomunicações na Califórnia no segundo trimestre de 2022. Cada registro representa um cliente e contém detalhes sobre dados demográficos, localização, mandato, serviços de assinatura, status do trimestre (ingressado, mantido ou desligado) e muito mais!
A tabela População de CEP contém informações complementares sobre as populações estimadas para os CEPs da Califórnia na tabela Rotatividade de Clientes."
Analisando o dataset, nota-se que este tem como objetivo obter informações e insights sobre as causas da rotatividade da empresa fictícia que foi denominada Telecom. Ao abrir a base de dados no PowerQuery, optou-se pela substituição dos valores em branco por valores como "No" ou "None" devido à grande quantidade destes em algumas categorias e também por ser mais coerente com o que o próprio dicionário do dataset forneceu como explicação. Exemplo: "Customer Churn, Premium Tech Support, Indica se o cliente subscreve um plano de suporte técnico adicional da empresa com tempos de espera reduzidos: Sim, Não (se o cliente não estiver subscrito ao serviço de Internet, será Não)". Após alguns ajustes, começou-se a elaborar o que seria colocado na apresentação. Os objetivos propostos foram:
- Trazer informações claras e relevantes sobre o conteúdo presente nesta base de dados.
- Evidenciar as perdas geradas pelo churn.
- Destacar comparações entre dados quantitativos e qualitativos do dataset com os clientes que cancelaram sua assinatura com a empresa.
- Analisar os possíveis motivos que podem estar gerando essa rotatividade de clientes.
- Trazer insights e possíveis soluções para o problema.

# **DESENVOLVIMENTO**
Iniciou-se elaborando uma página de relatório de Perfil de Cliente para conhecer o público. Foram colocadas as informações básicas da base de dados como: Total de Clientes, Intervalo de Idade, Estado Civil, Gênero e um mapa de calor com a localidade.
Considerando nesta etapa o total de clientes, foi inserida uma segmentação de dados para filtrar ao controle do usuário e permitir avaliar estes mesmos dados de acordo com o seu Status. Assim, já é possível para o usuário ter uma ideia entre os novos clientes, os que ficaram e os que saíram em relação ao próprio perfil.

Na página de "Serviços e Contratos", o foco foi expor os serviços utilizados pelos clientes, mas com uma abordagem mais direta, trazendo informações usando uma medida que calcula a porcentagem de clientes que saíram da empresa. Assim, todas as categorias de serviços e contratos dispostas ali já se relacionam com a rotatividade. Um exemplo claro é visualizar o gráfico de barras que correlaciona a rotatividade com as ofertas oferecidas aos usuários, onde nota-se que 52% dos usuários que aceitaram a oferta E de assinatura cancelaram a sua assinatura em algum momento.
Obs: No gráfico de serviços adicionais, foi colocado um botão em formato de bandeira onde, ao clicar, o usuário é direcionado a uma página oculta que traz os detalhes dos serviços adicionais, proporcionando uma maior granularidade e assistência na avaliação dos motivos da rotatividade através de um gráfico interativo que o usuário pode percorrer com os botões à esquerda.
A terceira página teve como objetivos: trazer os dados financeiros e o impacto gerado pela saída dos clientes da empresa e avaliar se as cobranças realizadas influenciaram na decisão de saída.
Obs: Assim como na página anterior (só que desta vez no cartão), é possível realizar uma avaliação mais minuciosa clicando no botão com ícone de bandeira, direcionando o usuário a outra página oculta contendo uma tabela com as razões e motivos apresentados pelos próprios clientes para o cancelamento da assinatura.
A decisão pelas cores se deu através de uma paleta gerada pelo site [Site de onde foi retirada a palheta de cores](https://coolors.co/) e a tela de fundo, que serviu como base para as visualizações, foi feita utilizando Figma. Para auxiliar na criação das visualizações, foram criadas medidas através de fórmulas DAX:
- Número total de clientes;
- Total de clientes que cancelaram assinatura;
- Porcentagem de clientes em relação ao total que saíram da empresa;
- Porcentagem de clientes que cancelaram sua assinatura em relação ao motivo pelo qual fizeram o cancelamento.
Também houve a necessidade de elaborar colunas calculadas como o Intervalo de Idade para a criação de um gráfico de barras semelhante a um histograma que possibilita verificar a distribuição dos clientes pela sua idade, e uma coluna que filtra os serviços adicionais disponibilizados, trazendo como Sim qualquer cliente que tenha algum serviço adicional em sua assinatura.
Há um total de 7.043 clientes, dentre os quais o gênero está dividido aproximadamente pela metade, assim como o estado civil, onde metade dos clientes são casados e a outra metade não. Além disso, mais de 75% dos clientes não têm dependentes e o intervalo de idade está bem distribuído.
Como descrito no dicionário do dataset, todos os clientes são da costa da Califórnia e o mapa de calor traz à tona esta informação, revelando também que a maior concentração deles está nas cidades de Los Angeles, São Francisco e San Diego, respectivamente.
Ao avaliar a quantidade de clientes que cancelaram suas assinaturas clicando em 'Churned', alguns pontos chamam a atenção:
Apesar do gênero continuar bem distribuído entre os clientes que cancelaram assinaturas, o número de clientes solteiros é 15% maior.
O intervalo de idade apresenta uma mudança em sua distribuição, onde os clientes com 60 anos ou mais são responsáveis pela maior parte dos cancelamentos (e também pelo menor número de entradas, como pode ser verificado ao clicar em 'Joined').
No número de dependentes, nota-se um acentuamento do cancelamento entre os clientes sem dependentes.
Nenhuma alteração significativa pode ser observada no mapa de calor.
Em Custos e Receitas, as primeiras informações visualizadas são referentes à receita total da empresa e à porcentagem de rotatividade de clientes, permitindo se aprofundar nas razões que os levaram ao cancelamento de seus planos.
Obs: Ao clicar na categoria 'Churned' em qualquer gráfico, o relatório mostra o quanto da receita foi perdida com os clientes que cancelaram os planos da empresa Telecom.
Nesta página, observa-se também que os clientes que cancelaram seus planos tiveram:
- Menos reembolsos do que os clientes que ficaram;
- Menor tempo de assinatura do que os clientes que permaneceram;
- Cobranças extras similares às dos que ficaram;
- Cobranças mensais maiores do que as dos que permaneceram;
Na página oculta, onde se visualiza a matriz com as categorias, razões e o quanto cada uma impactou a rotatividade, constata-se que 841 de 1.891 clientes que cancelaram os serviços da empresa migraram devido ao fato de os competidores oferecerem aparelhos melhores, melhores ofertas, mais dados e mais velocidade para download.
Porém, deve-se ter cautela nas análises, pois, embora a categoria 'Competidor' seja responsável por mais cancelamentos, ao verificar as razões especificamente, algumas chamam a atenção por ultrapassarem em número de cancelamentos os motivos da categoria 'Competidor'.

Na página de Serviços e Contratos, nota-se que o cancelamento de assinaturas foi maior na parcela de clientes que utilizam serviços adicionais. No relatório de detalhamento, que busca trazer um foco maior aos serviços adicionais oferecidos e sua relação com os cancelamentos, observa-se que o serviço de internet vem desagradando os usuários, pois aproximadamente 32% dos clientes que o utilizam realizaram cancelamento. Destes, quase metade (40%) utilizam fibra ótica.
Para os serviços de telefone, os resultados se equiparam em relação à assinatura, mas se distinguem em relação à quantidade de dados disponíveis para uso, onde 32% das pessoas que utilizavam deste serviço cancelaram.
Para as opções de Suporte e Segurança, chama a atenção que em todos os quesitos a porcentagem de cancelamento foi maior entre os clientes que não optaram por segurança extra ou suporte premium.
O inverso acontece com as opções de entretenimento, que apresentam uma pequena diferença, pendendo mais para os usuários que faziam uso deste serviço, sugerindo uma possível ligação com os usuários que fazem uso de Dados Ilimitados.
Em relação às ofertas, mais da metade dos usuários que aceitaram a Oferta E cancelaram o serviço.
Sobre os contratos, é possível avaliar que quanto mais longo for o contrato, menor a rotatividade dos clientes.
No método de pagamento, o cartão de crédito foi responsável pelas menores taxas de cancelamento.

# **CONCLUSÕES**
Partindo do pressuposto que nenhum cliente satisfeito cancelaria sua assinatura com a empresa, é necessário uma avaliação criteriosa dos serviços, ofertas e contratos oferecidos, começando obviamente pelos quais foram observados como os maiores responsáveis pelos cancelamentos.
Em uma análise geral das páginas do relatório, chega-se a denominadores comuns: o contrato Mês-a-Mês e o Serviço de Internet.

### Contrato Mês-a-Mês
É em razão deste contrato que se observa que a cobrança mensal dos clientes que saíram é mais alta (contratos de assinaturas mensais são mais caros), que a fidelidade em meses é mais de 2x menor que a dos clientes que ficaram e que, independentemente da oferta, as maiores taxas de cancelamento sempre provêm deste mesmo contrato. Isso pode ser observado ao selecionar este tipo de contrato na terceira página do relatório.
Este contrato também explica as razões mais votadas pelos clientes ao responderem o questionário que justifica sua saída da empresa: melhores ofertas pelo competidor e melhores dispositivos oferecidos pelo competidor.
Ações como valores menores ou melhores dispositivos oferecidos neste tipo de contrato podem ser a solução.

### Serviço de Internet
Usuários que utilizam o Serviço de Internet cancelam mais assinaturas do que os que não utilizam, independentemente do contrato assinado ou do perfil do consumidor, e ele parece estar afetando outros indicadores, elevando a taxa de cancelamento de clientes que possuem Dados Ilimitados e Streamings.
As tratativas devem ser realizadas para todos os tipos disponíveis, mas começando pela fibra ótica, onde 40% dos clientes que utilizaram deste serviço optaram pelo cancelamento.

## **PONTOS DE ATENÇÃO!**
Independentemente do motivo pelo qual os clientes estejam procurando o suporte da empresa, é necessário um novo treinamento dos colaboradores. Obviamente, a melhora dos contratos e serviços já citados fará com que os clientes procurem menos o suporte ou que eles estejam menos 'enviesados' pelo fato de procurarem o suporte já preparados para reclamarem, mas o indicador de insatisfação dos clientes quanto à atitude do suporte ainda merece atenção.
O fato de detectar uma disparidade tão grande entre as ofertas (especialmente a oferta E) pode estar relacionado a estarmos 'forçando' o cliente a realizar uma assinatura.
Segundo o dicionário do dataset, a Oferta E é a última oferta feita ao consumidor antes da desistência. Ela não possui uma média de cobrança maior que as outras e não foi observada nenhuma outra divergência, exceto uma relação com os contratos Mês-a-Mês:
- 805 clientes optaram pela Oferta E;
- Destas, 726 (90%!) optaram pelo contrato Mês-a-Mês;
Talvez a insistência pela aquisição de novos clientes esteja direcionando-os a um contrato com menos benefícios e menos vantagens e, após uma decepção com os serviços de internet oferecidos, eles cancelem a assinatura.




# **INTRODUCTION**
This dataset contains 2 CSV tables, sourced from Kaggle at: [Dataset URL](https://www.kaggle.com/code/tmadjid/telecom-churn-eda)
"The Customer Churn table contains information about all 7,043 customers of a telecommunications company in California for the second quarter of 2022. Each record represents a customer and includes details about demographics, location, tenure, subscription services, quarterly status (joined, retained, or churned), and more!
The ZIP Code Population table provides complementary information on the estimated populations for California ZIP codes in the Customer Churn table."
Analyzing the dataset, it is noted that its goal is to obtain information and insights about the causes of churn for the fictional company named Telecom. When opening the database in PowerQuery, blank values were replaced with values such as "No" or "None" due to the high quantity of these in some categories and also because it is more consistent with the dataset dictionary’s explanations. Example: "Customer Churn, Premium Tech Support, Indicates if the customer subscribes to an additional technical support plan from the company with reduced wait times: Yes, No (if the customer is not subscribed to the Internet service, it will be No)". After some adjustments, the preparation for the presentation began. The proposed objectives were:
- Provide clear and relevant information about the contents of this dataset.
- Highlight the losses generated by churn.
- Show comparisons between quantitative and qualitative data in the dataset with customers who canceled their subscriptions with the company.
- Analyze possible reasons for customer churn.
- Offer insights and possible solutions to the problem.

# **DEVELOPMENT**
We started by creating a Customer Profile report page to understand the audience. Basic database information was included, such as: Total Customers, Age Range, Marital Status, Gender, and a heatmap of the location.
Considering the total number of customers at this stage, a data segmentation filter was added for user control to evaluate the same data according to their Status. This allows the user to have an idea of new customers, retained customers, and churned customers in relation to their profile.

On the "Services and Contracts" page, the focus was to display the services used by customers more directly, providing information using a measure that calculates the percentage of customers who churned. Thus, all service and contract categories listed are already related to churn. A clear example is the bar chart that correlates churn with the offers provided to users, where it is noted that 52% of users who accepted Offer E canceled their subscriptions at some point.
Note: In the additional services chart, a flag-shaped button was added that directs the user to a hidden page with details on additional services, providing more granularity and assistance in evaluating churn reasons through an interactive chart that the user can navigate using buttons on the left.
The third page aimed to provide financial data and the impact of customer churn on the company, and to evaluate whether the charges influenced the decision to leave.
Note: Similar to the previous page (but this time with a card), a more detailed evaluation can be performed by clicking the flag icon button, directing the user to another hidden page containing a table with the reasons and motives presented by customers for canceling their subscriptions.
The color scheme was chosen using a palette generated by [pallete generator URL](https://coolors.co/) and the background, used as a base for the visualizations, was created using Figma. To assist in creating the visualizations, measures were created using DAX formulas:
- Total number of customers;
- Total number of churned customers;
- Percentage of churned customers relative to the total;
- Percentage of churned customers by reason for churn.
It was also necessary to create calculated columns such as Age Range for a bar chart similar to a histogram, allowing the distribution of customers by age to be verified, and a column filtering additional services available, showing "Yes" for any customer with additional services in their subscription.
There are a total of 7,043 customers, with gender approximately split evenly, as is marital status, with half the customers being married and the other half not. Additionally, over 75% of customers have no dependents, and the age range is well distributed.
As described in the dataset dictionary, all customers are from the California coast, and the heatmap reveals this, also showing the highest concentrations in Los Angeles, San Francisco, and San Diego, respectively.
When evaluating the number of churned customers by clicking 'Churned', some points stand out:
Despite gender remaining evenly distributed among churned customers, the number of single customers is 15% higher.
The age range shows a shift in distribution, with customers aged 60 and above accounting for the majority of churns (and also the fewest new customers, as seen by clicking 'Joined').
For dependents, churn is more pronounced among customers without dependents.
No significant changes are observed in the heatmap.
In Costs and Revenues, the initial information viewed relates to the company's total revenue and the churn rate, allowing deeper exploration of the reasons for plan cancellations.
Note: Clicking 'Churned' in any chart shows the lost revenue from customers who canceled their Telecom plans.
This page also shows that churned customers had:
- Fewer refunds than retained customers;
- Shorter subscription periods than retained customers;
- Similar extra charges to retained customers;
- Higher monthly charges than retained customers;
In the hidden page, viewing the matrix with categories, reasons, and the impact on churn, it is noted that 841 of the 1,891 churned customers left due to competitors offering better devices, better deals, more data, and faster download speeds.
However, caution is advised in analyses, as even though the 'Competitor' category accounts for most churns, some specific reasons surpass the 'Competitor' category in the number of cancellations.
On the Services and Contracts page, churn is higher among customers using additional services. In the detailed report focusing on additional services and their relation to churn, it is noted that the internet service is dissatisfying users, with approximately 32% of customers using it having canceled. Of these, almost half (40%) use fiber optic.
For telephone services, results are similar regarding subscriptions but differ in data availability, with 32% of users canceling.
For Support and Security options, churn is higher among customers not opting for extra security or premium support.
Conversely, entertainment options show a small difference, leaning towards users of this service, suggesting a possible link with Unlimited Data users.
Regarding offers, more than half of users who accepted Offer E canceled the service.
For contracts, it is observed that the longer the contract, the lower the churn.
For payment methods, credit cards had the lowest churn rates.

# **CONCLUSIONS**
Assuming that no satisfied customer would cancel their subscription, a thorough evaluation of the services, offers, and contracts provided is necessary, starting with those identified as major churn drivers.
A general analysis of the report pages reveals common denominators: the Month-to-Month contract and the Internet Service.

### Month-to-Month Contract
This contract shows higher monthly charges for churned customers (monthly subscriptions are more expensive), loyalty in months is more than twice as low as retained customers, and regardless of the offer, the highest churn rates always come from this contract. This can be seen by selecting this contract type on the third report page.
This contract also explains the top reasons cited by customers for leaving: better competitor offers and better devices offered by competitors.
Actions such as lower prices or better devices offered for this contract type may be the solution.

### Internet Service
Users of the Internet Service cancel more subscriptions than non-users, regardless of the signed contract or customer profile, and it seems to affect other indicators, raising the churn rate for customers with Unlimited Data and Streaming services.
Measures should be taken for all available types, starting with fiber optic, where 40% of users opted for cancellation.

## **POINTS OF ATTENTION!**
Regardless of the reason customers seek support, new staff training is necessary. Improving the already mentioned contracts and services will reduce support calls and reduce customer predisposition to complain. However, the dissatisfaction with support staff attitudes still warrants attention.
The significant disparity between offers (especially Offer E) may be related to pressuring customers into subscriptions.
According to the dataset dictionary, Offer E is the final offer made to consumers before giving up. It does not have a higher average charge than others, and no other discrepancies were observed except a relation with Month-to-Month contracts:
- 805 customers opted for Offer E;
- Of these, 726 (90%!) chose the Month-to-Month contract;
Perhaps pushing for new customers leads them to a contract with fewer benefits and advantages, and after disappointment with the internet services, they cancel their subscription.
