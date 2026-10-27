# Mini-Projeto de Análise de Dados - Varejo

# Sobre o projeto:

Primeiro projeto desenvolvido durante o curso Manipulação de Dados com Python e SQL no Senai/SC. A análise foi desenvolvida com Python, utilizando técnicas de limpeza, organização, análise exploratória e visualização dos dados.

# Objetivo:

- Explorar uma base de dados de varejo e praticar conceitos de análise de dados utilizando Python; 
- Explorar o perfil dos clientes;
- Identificar padrões de consumo;
- Analisar a relação entre o número de filhos dos clientes e suas compras.

# Dados e preparação:

- A base de dados passou por etapas de preparação para melhorar a qualidade e consistência das informações, incluindo:

* Renomeação e organização das colunas
*Verificação de valores ausentes e inconsistências
* Identificação de registros duplicados
* Ajuste dos tipos de dados
* Organização dos dados por cliente para evitar contagens repetidas nas análises do perfil familiar

# Análise exploratória:

Foram calculadas estatísticas descritivas para compreender a distribuição do número de filhos entre os clientes únicos.

# Número de filhos e categorias de produtos

Nesta etapa, são comparadas as categorias de produtos compradas por clientes com diferentes números de filhos. A pergunta é: Existem diferenças nas categorias compradas entre os grupos de clientes?

Os principais resultados dessa comparação foram acrescentados após a análise dos dados.

# Arquivos:

- Base Varejo.csv: base de dados utilizada no projeto, disponível em <https://www.kaggle.com/datasets/namespaiva/base-varejo/data?select=Base+Varejo.csv>;

- Mini_Projeto_Juliana_Lhullier_Borghetti_v7.ipynb: notebook com o código e análises;

- README_Juliana_Lhullier_Borghetti_v7.md: o presente arquivo, contendo explicações sobre o projetos, reflexões teóricas e insights obtidos a partir da análise dos dados.

# Ferramentas:

- Kagglehub
- Pandas
- Python
-Jupyter Notebook
- Visual Studio Code
- GitHub
_ GitHub Desktop

# Como executar

1. Clone ou baixe este repositório
2. Instale as bibliotecas necessárias
3. Abra o arquivbo de análise no VS Code ou ambiente Jupyter
4. Execute as células ou etapas do código na ordem apresentada

# Autora: Juliana Lhullier Borghetti

###### ETAPAS ######

# Primeiros passos:

- Importei o kagglehub;
- Importei a biblioteca pandas;
- Fiz a leitura do arquivo csv com pandas;
- Fiz o download do csv Kaggle e salvei no meu computador;
- Organizei os dados dentro da tabela, conforme orientação do professor;
- Fiz este README;
- Fiz um reposítório do GitHub e comecei a dar commits;

- Visualizei as informações do DataFrame, observei que havia 4 colunas com todos os valores nulos e nenhum mais;
- Verifiquei as 5 primeiras linhas do DataFrame;
- Verifiquei as últimas 5 linhas do DataFrame;
- Verifiquei 5 linhas aleatórias dentro do DataFrame;
- Verifiquei o tamanho do DataFrame;
- Verifiquei os nomes das colunas;
- Verifiqueia coluna "filhos";

- Verifiquei no material de apoio o que significava cada coluna:

1. DATA: Data da compra;
2. CO_ID: Identificação do número de compra (número da nota fiscal);
3. CL_ID: Identificação do cliente (número do cliente);
4. CL_GENERO: Sexo biológico informado pelo cliente;
5. CL_EC: Estado civil do cliente:
1: Casado ou união estável;
2: Divorciado;
3: Separado;
4. Solteiro;
5: Viúvo.
6. CL_FHL: Número de filhos do cliente;
7. CL_SEG: Segmentação econômica do cliente (classe A, B ou C);
8. PR_ID: Código do produto (SKU) adquirido;
9. PR_CAT: Categoria do produto adquirido;
10. PR_NOME: Nome do produto adquirido.

# Limpeza de dados:

- Antes de tudo, resolvi criar uma cópia do csv (df_varejo_limpo);

- Para melhor compreensão, renomeei e verifiquei as colunas:
    "DATA": "data",
    "CO_ID": "ID_compra",
    "CL_ID": "ID_cliente",
    "CL_GENERO": "genero_cliente",
    "CL_EC": "estado_civil",
    "CL_FHL": "numero_filhos",
    "CL_SEG": "classe_economica",
    "PR_ID": "codigo_produto",
    "PR_CAT": "categoria_produto",
    "PR_NOME": "nome_produto"

- Como apareceram várias colunas "Unnamed", resolvi verificar se essas colunas estavam vazias. Resolvi verificar todos os valores ausentes no DataFrame;
- Aparentemente as colunas "Unnamed" estavam vazias (usando isna()), mas resolvi investigar mais a fundo;
- Verifiquei todas (all) as colunas vazias (isna) e criei uma variável (colunas_vazia) para armazenar esses resultados;
- Imprimi a contagem (len), o nome das colunas vazias e pedi uma lista;
- Optei por remover as colunas totalmente vazias com dropna(), pois considerei que não tinham utilidade para análise e podiam inclusive me confundir;
- Verifiquei novamente os valores ausentes em todas as colunas do DataFrame, não havia;

- Verifiquei duplicatas no DataFrame completo, depois por coluna "ID_compra" e então por linhas completas para garantir que não havia registros duplicados;
- 830.000 linhas sem dados ausentes e 184.330 linhas duplicadas foram detectadas quando verifiquei duplicatas no DataFrame completo;
- Havia 811.529 duplicados na coluna "ID_compra";
- Resolvi verificar então registros duplicados nas colunas "data", "ID_compra", "ID_cliente" e "nome_produto", pois parecia ser a mesma compra, pelo mesmo cliente, mas poderiam ser diferentes produtos. 
- Havia ainda 176.327 linhas duplicadas no DataFrame. 
- Resolvi verificar registros duplicados nas colunas "data", "ID_compra", "ID_cliente" sem "nome_produto"
- Havia novamente 811.529;
- Resolvi verificar então registros duplicados verificando cada uma delas, todas as colunas;
- Havia 96.553 duplicatas;

- Fiz uma investigação comparando o total de linhas únicas e linhas duplicadas. Depois separei as linhas duplicadas para análise. Não consegui resolver, pedi ajuda para o professor.
- Linhas duplicadas:  184.330
- Linhas únicas:  733.447
- Com a ajuda do professor e colegas, entre as opções .drop_duplicates() e .nunique(), optei por fazer os dois para conferir. O drop_duplicates foi a solução.
- Apesar de não haver valores vazios de acordo com as informações já obtidas com .info(), conferi a soma dos valores vazios com .isna() na coluna "categoria_produto", visto que era pedido na documentação do mini-projeto "usar a lógica (if/else) para preencher as categorias vazias com "Sem Categoria"";

- Verifiquei (com a ajuda do professor) que havia os valores "#N/D" nas colunas "categoria_produto" e "nome_produto". Usei a lógica (if/else) para preencher as categorias com "#N/D" substituindo por "Sem Categoria";
- Com o DataFrame limpo, verifiquei novamente os tipos de dados;
- Verifiquei os tipos de dados e inconsistêcias nas colunas str (string) usando .unique() para conferir se havia caracteres especiais, letras minúsculas, variações que pediriam tratamento. Não havia.

 # Módulo Datetime

 - Importei a classe date do módulo datetime;
- Conferi o formato e tipo de dados da coluna "data";
 -  Converti o texto para datetime (validei a regra do identificador de número de compra, convertendo a string de data da compra utilizando o módulo datetime)
- Conferi a conversão;
- Conferi se há algum valor nulo após a conversão;
-  Conferi algumas linhas para garantir;
- Conferi as informações para ter certeza.

 # Estatísticas

- Conforme havia percebido anteriormente, o número de filhos por cliente se repetia. Assim, as estatísticas provenientes exclusivamente da coluna "numero_filhos" não seriam confiáveis;
- Por essa razão, comparei a quantidade de clientes únicos com a quantidade de linhas na coluna do número de filhos ("ID_cliente" e "numero_filhos");
- Havia apenas 1.000 clientes únicos para 733.447 registros do número de filhos;
- Agrupei um único valor de número de filhos por cliente usando o groupby() para cruzar os dados das duas colunas ("ID_cliente" e "numero_filhos") e o .first() para selecionar o primeiro valor não-nulo de filhos para cada cliente;
-  Contei quantos clientes tinham cada número de filhos (0, 1, 2, 3, 4) usando value_counts() e pedi para ordenar em ordem crescente com .sort_index(ascending=False);
- Assim, verifiquei que: 527 cliente não tinham filhos, 125 clientes tinham 1 filho, 130 clientes tinham 2 filhos, 121 clientes tinham 3 filhos e 97 clientes tinham 4 filhos;
- Utilizei "estatísticas descritivas básicas para a coluna de número de filhos do cliente (média; mediana; desvio padrão; máximo; mínimo; e contagem, quartis)" propostas para o mini-projeto;
- Como describe não traz a moda, fiz separadamente usando .mode();
- Para melhor visualização, fiz a mesma operação com print(), levando em conta as seguintes estatísticas:
* Contagem (count) = Das 733.447, foram considerados 1.000 clientes únicos;
* Mínimo (min) = O valor mínimo de filhos encontrado foi zero (sem filhos);
* Máximo (max) = O número máximo de filhos foi 4;
* Média (mean) = A soma do número total de filhos dividido pelo número de registros válidos resultou na média de 1.14 filhos por cliente;  
* Desvio padrão (std) = O desvio padrão do número de filhos foi de cerca de 1.41, indicando uma dispersão dos valores em relação á média;
* Quartis (Q1, Q2, Q3, Q4) = Até 50% dos cliente não tem filhos, 75% tem até 2 filhos e o restante dos cliente têm 3 a 4 filhos;
* Mediana .mode() = O valor que aparece com maior frequência é de 0 filhos.

 # Padrões de agrupamento 
 
 - Conforme orientação para o mini-projeto, explorei padrões de agrupamento "com pelo menos dois agrupamentos (por exemplo: gênero com mais vendas, compras), usando groupby() ou pivot_table()";
 - Contei os registros de compra combinando a categoria do produto com o número de filhos com o objetivo de analisar a relação entre o tipo de produto comprado por clientes com nenhum, 1, 2, 3 ou mais filhos;
 - Calculei a categoria com maior percentual de compras para cada número de filhos;
 - Pedi para organizar em ordem descrescente para visualizar primeiro as categorias mais frequentes e o total de vendas ;
 - Considerando que um cliente pode comprar várias categorias, percebi que os totais dessas colunas não representavam necessariamente grupos de clientes. Desta forma, não pude associar o número de filhos com as preferências de compra;
 - Para calcular a proporção de clientes de cada grupo que comprou cada categoria, usei o pivot_table();
 -Criei uma tabela com pivot_table() cruzando duas variáveis - número de filhos e categoria do produto;
- Usei index para colocar o número de filhos nas linhas;
- Coloquei a categoria do produto na coluna com columns;
- Usei o aggfunc= "size" para contar os registros em cada combinação filhos-categoria;
- Pedi para colocar o número zero quando não houvesse registro com fill_value = 0.

- Limpei o código formatando texto, removendo células e ferramentas desnecessárias como as bibliotecas seaborn e matplotlib;
- Conferi, organizei e aprimorei o README.

 # Insights:

- Principais resultados:

* Clientes analisados: 1.000
* Média: 1, 14 filhos por cliente
* Mediana: zero filhos
* Desvio padrão: 1,41
* Mínimo: zero filhos
* Máximo: 4 filhos

 1. Considerando o desvio padrão de 1,41, com a média do número de filhos de 1.14 filhos por cliente e a mediana resultando em zero, percebe-se que o número de filhos não é igual para todos os cliente. No entanto entre os 1.000 clientes únicos, mais da metade (527) não tinha filhos. Enquanto 75%  (terceiro quartil) dos clientes tinha até 2 filhos. A diversidade de perfis familiares pode ser investigada para verificar se clientes com diferentes números de filhos apresentam preferências distintas por categoria ou produto específico;

 2. Ao analisar a relação entre o tipo de produto comprado por clientes com diferentes números de filhos, nota-se que o volume de compras por categoria se relaciona com a quantidade de clientes. Ou seja, os clientes sem filhos realizaram a maior parte das compras. Quando observadas as categoria de produtos, alimentos, seguidos de higiene, limpeza e bebidas (nessa ordem) representam as preferências de compra para todos os grupos. Dois grupos - sem filhos e com 2 filhos - consomem também produtos Pet. Todos os grupos consumiram produtos "Sem categoria", o que poderia valer investigar do que se tratam;  

 3. Ao analisar a relação entre número de filhos e a compra de produtos específicos, um registro chama a atenção: o quinto produto mais consumido por consumidores sem filhos foi "papinha infantil" (3.453). Fica a questão: clientes sem filhos consomem papinha ou há algum erro nos registros?;  

 4. Verifica-se ainda que a proporção das compras por categorias de produtos é bastante similar entre os grupos com diferentes números de filhos. Alimentos representam cerca de 52% das compras para todos os grupos, enquanto produtos Pet ficam por volta dos 4%. A empresa poderia pensar em uma exposição maior dos produtos Pet e das bebidas, que representam pouco mais de 5% das vendas. 
 
 Esses resultados ajudam a descrever o perfil familiar dos clientes.

# Próximos passos:

- Criar visualizações para facilitar a interpretação dos resultados;
- Aprofundar a comparação da distribuição das categorias e produtos entre os grupos familiares;
- Investigar outros padrões de compra presentes na base de dados.
 
# Conclusão:

A análise permitiu organizar e explorar a base de dados de compras, identificando características importantes do perfil dos clientes. Entre os principais resultados, destaca-se a predominância de clientes sem filhos, com média de 1,14 filhos por cliente e mediana igual a zero. Essas informações contribuem para uma melhor compreensão da base analisada.

A comparação entre o número de filhos e as categorias de produtos compradas representa uma etapa relevante para investigar semelhanças e diferenças nos padrões de consumo entre os grupos. No entanto, esta análise ainda precisa ser aprofundada com resultados quantitativos e visualizações específicas. Dessa forma, o mini-projeto estabelece uma base para análises futuras e para a identificação de relações mais detalhadas entre as características dos clientes e seus hábitos de compras.
