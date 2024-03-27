# Vendas Internas da Empresa

## Case de Planejamento da Empresa Co.

Você desempenha o papel de um analista de Inteligência de Dados e Automatização no setor de Vendas Internas da Empresa.
Sua responsabilidade como analista é supervisionar a adequada governança e processamento dos dados, assegurando sua integridade e clareza operacional, elaborando relatórios, consultas e scripts para automatizar procedimentos, aprimorando a eficácia operacional e possibilitando uma gestão de resultados com qualidade.

Nesta semana, seu objetivo é formular o procedimento para estabelecer metas e avaliar os resultados mensais. Para isso, é necessário aderir às diretrizes operacionais a fim de criar tabelas que facilitem o acompanhamento das metas e resultados pela equipe, desde os representantes de vendas até os gestores e todo o departamento de Vendas Internas, por meio de um painel de controle (dashboard).

Para realizar essa missão, você terá acesso aos documentos conforme detalhado abaixo. Certifique-se de ler atentamente as instruções contidas em cada documento e seguir as regras operacionais.


## Arquivos

### Arquivo 1 - fact_leads.csv
O arquivo fact_sales.csv possui registros em que cada linha representa um lead no mês de janeiro de 2077 com dados de Agent_ID (id do vendedor responsável pela venda) e Date (data da venda).  \
Obs: Leads são potenciais clientes que entram em contato com a intenção de adquirir uma máquina.

### Arquivo 2 - fact_sales.csv
O arquivo fact_sales.csv possui registros em que cada linha representa uma venda no mês de janeiro de 2077 com dados de Agent_ID (id do vendedor responsável pela venda) e Date (data da venda).

### Arquivo 3 - dim_agents.csv
O arquivo dim_agents.csv possui registros em que cada linha representa um agente. \
Segue abaixo o schema desta tabela:
- Agent_ID é o Id do agente comercial;
- lider é o id do líder do agente comercial;
- nivel representa o nível do agente comercial, podendo variar de 1 a 5 e define o fator multiplicativo da meta de produtividade que é baseada no nível 1;
- folga_1 representa o primeiro dia da semana em que o agente não trabalha, e consequentemente não tem meta;
- folga_2 representa o segundo dia da semana em que o agente não trabalha, e consequentemente não tem meta;
- canal representa a forma de contato em que o agente atende os leads. Cada canal possui uma meta específica.
- funcao é a descrição de que este ID representa um vendedor.

### Arquivo 4 - dim_leaders.csv
O arquivo dim_leaders.csv possui registros em que cada linha representa um lider.
- Lider_ID é o Id do lider comercial;
- lider_de_operacao é o id do líder de operação do lider comercial;
- funcao é a descrição de que este ID representa um líder.



## Regras de negócio

A meta possui sua menor granularidade na unidade de DIA. O cálculo da meta diária é dado multiplicando o fator multiplicativo do nível pela meta diária do canal. \
ex: Um agente do canal whatsapp, do nível 2 tem como meta diária 4*1,1 = 4,4.

Abaixo seguem os valores dos fatores para o cálculo da meta.

Meta por nível:
- nível 1 = 100%;
- nível 2 = 110%;
- nível 3 = 120%;
- nível 4 = 125%;
- nível 5 = 130%.

Meta diária por canal para o nível 1:
- chat = 3;
- whatsapp = 4;
- telefone = 3,7.

Os agentes possuem metas apenas nos dias em que não possuem folga. Ou seja, no dia de folga, a meta é zero. Em feriados nacionais também não há meta, porém há a prática de realização da escala extra, em que pessoas trabalham com hora-extra para aumentar o resultado mensal.

Para agentes que trabalham no domingo, há uma regra em que após três domingos trabalhados, o colaborador deve ter um domingo de folga. Para isso, considere que o primeiro domingo trabalhado do time será dia 03/01/2077.


## Entregas

Com base nos Arquivos e descrições, siga os seguintes passos:

1. Em Python, com os arquivos fornecidos, crie uma tabela de metas para cada agente para cada dia do mês de janeiro de 2077. Não há meta para folgas fixas nem para feriados. A tabela deve conter pelo menos as colunas de Data (ex: 2077-01-01), Agent_ID (ex: 1), dia da semana (ex: segunda-feira), Meta (ex: 4), trabalha (ex: True, False) e deve respeitar essa granularidade. \
Obs: Nos dias em que um determinado agente não possui meta, a linha deve estar presente na tabela com o valor da coluna Meta = 0 e trabalha = False.

3. Construa uma tabela relacionando a tabela da tarefa anterior com o resultado das tabelas de vendas e leads para cada dia de cada vendedor.

4. Utilizando a ferramenta que julgar mais adequada, crie uma dashboard operacional, para que os vendedores e líderes possam acompanhar seus resultados de forma eficiente, fornecendo insights e insumos para melhorarem dia após dia.

5. Na dashboard, crie uma lista contendo o ID de cada agente e seu respectivo atingimento (vendas/meta) em porcentagem, para apuração da meta.
